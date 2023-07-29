# Multicall

For any write function, the SDK includes a corresponding call data version that returns the call data information instead of submitting a transaction. These objects can then be aggregated and passed into the [`multicall`](multicall.md#multicall) function in order to batch multiple operations into one transaction.

### <mark style="color:purple;">multicall</mark>

Batch multiple write operations in one transaction.

```typescript
const multicallResult = await hatsClient.multicall({
    account,
    calls,
});
```

_**Arguments**_:

```typescript
{
    account: Account | Address;
    calls: {
      functionName: string;
      callData: Hex;
    }[];
}
```

* `account` - Viem account (Address for JSON-RPC accounts or Account for other types).
* `calls` - An array of call data objects, each one includes the function name and the call data to pass to the function.

_**Response**_:

```typescript
{
  status: "success" | "reverted";
  transactionHash: `0x${string}`;
  gasUsed: bigint;
  hatsCreated: bigint[];
  hatsMinted: {
    hatId: bigint;
    wearer: `0x${string}`;
  }[];
  hatsBurned: {
    hatId: bigint;
    wearer: `0x${string}`;
  }[];
  hatStatusChanges: {
    hatId: bigint;
    newStatus: "active" | "inactive";
  }[];
  wearerStandingChanges: {
    hatId: bigint;
    wearer: `0x${string}`;
    newStanding: "good" | "bad";
  }[];
}
```

* `status` - "success" if transaction was successful, "reverted" if transaction reverted.
* `transactionHash` - transaction's hash.
* `gasUsed` - Amount of gas used in the transaction.
* `hatsCreated` - Hats IDs of any newly created hats.
* `hatsMinted` - For every hat minted, contains an object with the hat ID and the new wearer address.
* `hatsBurned` - For every hat burned, contains an object with the hat ID and the wearer address.
* `hatStatusChanges` - For every hat status change, contains on object with the hat ID and the new status.
* `wearerStandingChanges` - For every wearer standing status change, contains an object with the hat ID, the wearer address and the new standing.

_**Example:**_

Create a new top-hat, then create one child hat and mint the child hat to a new wearer.

```typescript
const mintTopHatCallData = await hatsClient.mintTopHatCallData({
    target,
    details,
    imageURI,
});

const createHatCallData = await hatsClient.createHatCallData({
    admin,
    details,
    maxSupply,
    eligibility,
    toggle,
    mutable,
    imageURI,
});

const mintHatCallData = await hatsClient.mintHatCallData({
    hatId,
    wearer,
});

const multiCallResult = await hatsClient.multicall({
    account,
    calls: [mintTopHatCallData, createHatCallData, mintHatCallData],
});
```
