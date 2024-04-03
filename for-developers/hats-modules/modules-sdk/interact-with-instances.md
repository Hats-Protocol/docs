# Interact With Instances

The following functions provide utilities to support the interaction with module instances: checking whether a certain instance was created, reading instance's [display parameters](types.md#module) (as specified in the 'parameter' property in the Module's object) and calling its write functions.

To get the module's object from an instance address, use [this function](../../modules-sdk/get-available-modules.md#getmodulebyinstance).

### <mark style="color:purple;">isModuleDeployed</mark>

Check if a module is already deployed, using its creation arguments.

```typescript
const isDeployed = await hatsModulesClient.isModuleDeployed({
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
boolean
```

`true` if the module was deployed, `false` otherwise.

### <mark style="color:purple;">getInstanceParameters</mark>

Get a module's instance live parameters.&#x20;

The parameters to fetch are listed in the [Module's registry object](types.md#module) (in the 'parameters' property), and their purpose is to display relevant information for each module instance.

```typescript
const module = await hatsModulesClient.getInstanceParameters(instance);
```

_**Arguments**_:

```typescript
instance: `0x${string}`
```

`instance` - Instance's address.

_**Response**_:

```typescript
{
  label: string;
  value: unknown;
  solidityType: string;
  displayType: string;
}[]
```

An array of objects, each containing a parameter's information:

* `label` - The parameter's name/description.
* `value` - The parameter's value, as was returned from the instance contract.
* `solidityType` - The parameter's Solidity type.
* `displayType`- The parameter's display type. Its purpose is for UIs to be able to render an appropriate component for the parameter. For example, rendering a date for timestamps.

### <mark style="color:purple;">callInstanceWriteFunction</mark>

Call a module's write function.

The 'customRoles' and 'writeFunctions' properties of a [Module's object](types.md#module) enable to programmatically get all the write functions of a module, together with any necessary information to call them: expected input arguments and the roles (Hats) that have the permission to call each function.

```typescript
const res = await hatsModulesClient.callInstanceWriteFunction({
    account,
    moduleId,
    instance,
    func,
    args,
});
```

_**Arguments**_:

```typescript
{
    account: Account | Address;
    moduleId: string;
    instance: Address;
    func: WriteFunction;
    args: unknown[];
}
```

* `account` - Viem account (Address for JSON-RPC accounts or Account for other types).
* `moduleId` - Module's ID (implementation address).
* `instance` - Instance's address.
* `func` - The function to call, provided as an object of [WriteFunction](types.md#writefunction) type.
* `args` - The input arguments to pass the function.

_**Response**_:

```typescript
{
  status: "success" | "reverted";
  transactionHash: `0x${string}`;
}
```

* `status` - "success" if transaction was successful, "reverted" if transaction reverted.
* `transactionHash` - transaction's hash.
