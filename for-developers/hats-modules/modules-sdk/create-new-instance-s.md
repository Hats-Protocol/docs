# Create New Instance/s

### <mark style="color:purple;">createNewInstance</mark>

Create a new module instance.

```typescript
const createInstanceResult = await hatsModulesClient.createNewInstance({
    account,
    moduleId,
    hatId,
    immutableArgs,
    mutableArgs,
    saltNonce,
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
    saltNonce?: bigint;
}
```

* `account` - Viem account (Address for JSON-RPC accounts or Account for other types).
* `moduleId` - The module ID (implementation address).
* `hatId` - The hat ID for which the module is created.
* `immutableArgs` - The module's immutable args. The arguments should be in the same order as in the [Module](types.md#module) object.
* `mutableArgs` - The module's mutable args. The arguments should be in the same order as in the [Module](types.md#module) object.
* `saltNonce` - Optional salt nonce to use. If not provided, will be randomly generated.

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

### <mark style="color:purple;">batchCreateNewInstances</mark>

Batch create new module instances.

Each module will be created according to the provided parameters, on the same corresponding array index.

```typescript
const createInstancesResult = await hatsModulesClient.batchCreateNewInstances({
    account,
    moduleIds,
    hatIds,
    immutableArgsArray,
    mutableArgsArray,
    saltNonces
});
```

_**Arguments**_:

```typescript
{
    account: Account | Address;
    moduleIds: string[];
    hatIds: bigint[];
    immutableArgsArray: unknown[][];
    mutableArgsArray: unknown[][];
    saltNonces?: bigint[]; 
}
```

* `account` - Viem account (Address for JSON-RPC accounts or Account for other types).
* `moduleIds` - The module IDs (implementation address).
* `hatIds` - The hat IDs for which the modules are created.
* `immutableArgsArray` - Each module's immutable arguments. For each module, the arguments should be in the same order as in the [Module](types.md#module) object.
* `mutableArgsArray` - Each module's mutable arguments. For each module, the arguments should be in the same order as in the [Module](types.md#module) object.
* `saltNonces` - Optional salt nonces to use. If not provided, will be randomly generated.

_**Response**_:

```typescript
{
  status: "success" | "reverted";
  transactionHash: `0x${string}`;
  newInstances: Array<`0x${string}`>;
}
```

* `status` - "success" if transaction was successful, "reverted" if transaction reverted.
* `transactionHash` - transaction's hash.
* `newInstances` - The address of the new module instances.

### <mark style="color:purple;">predictHatsModuleAddress</mark>

Predict a module's address before/after it was created, using its creation arguments.

```typescript
const predictedAddress = await hatsModulesClient.predictHatsModuleAddress({
    moduleId,
    hatId,
    immutableArgs,
    saltNonce,
});
```

_**Arguments**_:

```typescript
{
   moduleId: string;
   hatId: bigint;
   immutableArgs: unknown[];
   saltNonce: bigint;
}
```

* `moduleId` - Module's ID.
* `hatId` - The target hat ID, as provided to the [instance creation function](create-new-instance-s.md#createnewinstance).
* `immutableArgs` - The module's immutable args, as provided to the [instance creation function](create-new-instance-s.md#createnewinstance).
* `saltNonce` - Salt nonce to use.

_**Response**_:

```typescript
`0x${string}`
```

The predicted module address.
