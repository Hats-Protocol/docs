# Interact With Instances

The following functions provide utilities to support the interaction with module instances.&#x20;

To get the module's object from an instance address, use [this function](../../modules-sdk/get-available-modules.md#getmodulebyinstance).

### <mark style="color:purple;">predictHatsModuleAddress</mark>

Predict a module's address before/after it was created, using its creation arguments.

```typescript
const predictedAddress = await hatsModulesClient.predictHatsModuleAddress({
    moduleId,
    hatId,
    immutableArgs,
});
```

_**Arguments**_:

```typescript
{
   moduleId: string;
   hatId: bigint;
   immutableArgs: unknown[];
}
```

* `moduleId` - Module's ID.
* `hatId` - The target hat ID, as provided to the [instance creation function](create-new-instance-s.md#createnewinstance).
* `immutableArgs` - The module's immutable args, as provided to the [instance creation function](create-new-instance-s.md#createnewinstance).

_**Response**_:

```typescript
`0x${string}`
```

The predicted module address.

### <mark style="color:purple;">isModuleDeployed</mark>

Check if a module is already deployed, using its creation arguments.

```typescript
const isDeployed = await hatsModulesClient.isModuleDeployed({
    moduleId,
    hatId,
    immutableArgs,
});
```

_**Arguments**_:

```typescript
{
   moduleId: string;
   hatId: bigint;
   immutableArgs: unknown[];
}
```

* `moduleId` - Module's ID.
* `hatId` - The target hat ID, as provided to the [instance creation function](create-new-instance-s.md#createnewinstance).
* `immutableArgs` - The module's immutable args, as provided to the [instance creation function](create-new-instance-s.md#createnewinstance).

_**Response**_:

```typescript
boolean
```

`true` if the module was deployed, `false` otherwise.

### <mark style="color:purple;">getInstanceParameters</mark>

Get a module's instance live parameters.&#x20;

The parameters to fetch are listed in the module's registry object, and their purpose is to display relevant information for each module instance.

```typescript
const module = hatsModulesClient.getInstanceParameters(instance);
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

### <mark style="color:purple;">getFunctionsInModule</mark>

Get a module's functions from its ABI.

```typescript
const module = hatsModulesClient.getFunctionsInModule(moduleId);
```

_**Arguments**_:

```typescript
moduleId: string
```

`moduleId` - Module's ID.

_**Response**_:

```typescript
{
  name: string;
  type: "write" | "read";
  inputs: { name: string | undefined; type: string }[];
}[]
```

An array of objects, each containing a function's information:

* `name` - The function's name.
* `type` - "read" for "view" and "pure" functions, "write" otherwise.
* `inputs` - Array of inputs for the function. For each input, contains its name, and its Solidity type.
