# Creating New Instances

Create new Instances of a 1 of N Hats Account, and/or predict the addresses of accounts.

### <mark style="color:purple;">createAccount</mark>

Create a new 1 of N Hats Account instance.

```typescript
const createHatsAccountResult = await hatsAccount1ofNClient.createAccount({
    account,
    hatId,
    salt,
});
```

_**Arguments**_:

```typescript
{
    account: Account | Address;
    hatId: bigint;
    salt: bigint;
}
```

* `account` - Viem account (Address for JSON-RPC accounts or Account for other types).
* `hatId` - ID of the hat for which to create the account.
* `signersHatId` - arbitrary number as "salt".

_**Response**_:

```typescript
{
  status: "success" | "reverted";
  transactionHash: `0x${string}`;
  newAccount: `0x${string}`;
}
```

* `status` - "success" if transaction was successful, "reverted" if transaction reverted.
* `transactionHash` - transaction's hash.
* `newAccount` - In case of success, the address of the new account.

### <mark style="color:purple;">predictAccountAddress</mark>

Predict the address of a 1 of N Hats Account instance.

```typescript
const predictedAccount = await hatsAccount1ofNClient.predictAccountAddress({
    hatId,
    salt,
});
```

_**Arguments**_:

```typescript
{
    hatId: bigint;
    salt: bigint;
}
```

* `hatId` - ID of the hat for which to create the account.
* `signersHatId` - arbitrary number as "salt".

_**Response**_:

```typescript
`0x${string}`
```

The predicted account address.
