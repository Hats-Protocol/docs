# Claiming Hats

Hats can be made claimable by using the [Multi Claims Hatter](../../../hats-integrations/claiming-and-onboarding-integrations/making-hats-claimable.md) module.

The following functions support the claiming functionality enabled by this module.

### <mark style="color:purple;">accountCanClaim</mark>

Check whether an account can claim a given hat.

```typescript
const canClaim = await hatsClient.accountCanClaim({
    hatId,
    account,
});
```

_**Arguments**_:

```typescript
{
    hatId: bigint;
    account: Address;
}
```

* `hatId` - The hat ID to claim. &#x20;
* `account` - The claiming account's address.

_**Response**_:

```typescript
boolean
```

`true` if can claim, `false` otherwise.

### <mark style="color:purple;">canClaimForAccount</mark>

Check whether a hat can be claimed on behalf of a given account.

```typescript
const canClaimFor = await hatsClient.canClaimForAccount({
    hatId,
    account,
});
```

_**Arguments**_:

```typescript
{
    hatId: bigint;
    account: Address;
}
```

* `hatId` - The hat ID to claim-for. &#x20;
* `account` - The account address to claim on behalf of.

_**Response**_:

```typescript
boolean
```

`true` if can claim-for, `false` otherwise.

### <mark style="color:purple;">claimHat</mark>

Claim a hat for the calling account.

```typescript
const claimHatResult = await hatsClient.claimHat({
    account,
    hatId,
});
```

_**Arguments**_:

```typescript
{
    account: Account | Address;
    hatId: bigint;
}
```

* `account` - Viem account (Address for JSON-RPC accounts or Account for other types).
* `hatId` - ID of the hat to claim.

_**Response**_:

```typescript
{
  status: "success" | "reverted";
  transactionHash: `0x${string}`;
}
```

* `status` - "success" if transaction was successful, "reverted" if transaction reverted.
* `transactionHash` - transaction's hash.

### <mark style="color:purple;">claimHatFor</mark>

Claim a hat on behalf of a chosen account.

```typescript
const claimHatForResult = await hatsClient.claimHatFor({
    account,
    hatId,
    wearer,
});
```

_**Arguments**_:

```typescript
{
    account: Account | Address;
    hatId: bigint;
    wearer: Address;
}
```

* `account` - Viem account (Address for JSON-RPC accounts or Account for other types).
* `hatId` - ID of the hat to claim-for.
* `wearer` - Address for which to claim the hat for.

_**Response**_:

```typescript
{
  status: "success" | "reverted";
  transactionHash: `0x${string}`;
}
```

* `status` - "success" if transaction was successful, "reverted" if transaction reverted.
* `transactionHash` - transaction's hash.

### <mark style="color:purple;">multiClaimHatFor</mark>

Claim a hat on behalf of multiple accounts.

```typescript
const claimHatForResult = await hatsClient.multiClaimHatFor({
    account,
    hatId,
    wearers,
});
```

_**Arguments**_:

```typescript
{
    account: Account | Address;
    hatId: bigint;
    wearers: Address[];
}
```

* `account` - Viem account (Address for JSON-RPC accounts or Account for other types).
* `hatId` - ID of the hat to claim-for.
* `wearers` - Addresses for which to claim the hat for.

_**Response**_:

```typescript
{
  status: "success" | "reverted";
  transactionHash: `0x${string}`;
}
```

* `status` - "success" if transaction was successful, "reverted" if transaction reverted.
* `transactionHash` - transaction's hash.
