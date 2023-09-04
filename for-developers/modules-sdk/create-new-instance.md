# Create New Instance

### <mark style="color:purple;">createNewInstance</mark>

Create a new module instance.

```typescript
const createInstanceResult = await hatsModulesClient.createNewInstance({
    account,
    moduleId,
    hatId,
    immutableArgs,
    mutableArgs,
});
```

_**Arguments**_:

```typescript
{
    account: Account | Address;
    moduleId: string;
    hatId: bigint;
    immutableArgs: unknown[];
    mutableArgs: unknown[];
}
```

* `account` - Viem account (Address for JSON-RPC accounts or Account for other types).
* `moduleId` - The module ID.
* `hatId` - The hat ID for which the module is created.
* `immutableArgs` - The module's immutable args.
* `mutableArgs` - The module's mutable args.

_**Response**_:

```typescript
{
  status: "success" | "reverted";
  transactionHash: `0x${string}`;
  newInstance: `0x${string}`;
}
```

* `status` - "success" if transaction was successful, "reverted" if transaction reverted.
* `transactionHash` - transaction's hash.
* `newInstance` - In case of success, the address of the new module instance.
