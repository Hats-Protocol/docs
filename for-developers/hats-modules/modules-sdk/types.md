# Types

### <mark style="color:purple;">Module</mark>

Represents a module object, compatible with the registry's module objects.

```typescript
{
  name: string; // module's name
  deprecated?: boolean; // if 'true', indicates that new instances of this module should not be created
  details: string[]; // array of strings representing paragraphs that describe the module to end users.
  links: { // relevant links about the module
    label: string; // link's name
    link: string; // URL
  }[];
  parameters: { // module's dispaly parameters, chosen by its creator as relevant for dispaly to end users
    label: string; // parameter's name
    functionName: string; // name of the view or pure function that gets the parameter value
    displayType: string; // a free-text field that tells front ends how to generate a proper UI component for the parameter
  }[];
  type: { // type of module
    eligibility: boolean;
    toggle: boolean;
    hatter: boolean;
  };
  implementationAddress: string; // module's implementation address, equal in every network
  deployments: { // networks the implementation is deployed and supported
    chainId: string; // chain's ID
    block: string; // block number of the deployment transaction
  }[];
  creationArgs: ModuleCreationArgs; // the arguments that are passed to the module factory's creation function
  customRoles: Role[]; // module's custom roles
  writeFunctions: WriteFunction[]; // module's write functions
  abi: Abi; // module's ABI
}
```

### <mark style="color:purple;">Role</mark>

A module's custom role. Each module role is associated with a hat and grants permissions to the hat's wearer(s) to call certain functions on the module contract.

There are two special roles with a reserved ID that are automatically added to each module:

1. `public` role, associated with functions that are permitted to any caller
2. `hatAdmins` role, associated with functions that are permitted to the target hat's admins

```typescript
{
  id: string; // role's ID
  name: string; // role's name
  criteria: string; // The name of the contract function which can be used to retrieve the role's hat
  hatAdminsFallback?: boolean; // 'true' indicates that the role is granted to the target hat's admin(s) if/when the role's criteria function returns zero.
}
```

### <mark style="color:purple;">WriteFunction</mark>

The module's write functions. Each write function is associated with a role and grants permissions to the role's wearer(s) to call the function on the module contract.

```typescript
{
  roles: string[]; // IDs of the roles that have the authority to call the function
  functionName: string; // the name of the function in the contract
  label: string; // the name to be displayed to end users
  description: string; // a description of the function to be displayed to end users
  primary?: boolean; // 'true' indicates that this function is the primary function of the roles it is associated with. Front ends can use this information to display the function more prominently for each role
  args: WriteFunctionArg[]; // the arguments of the function
}
```

### <mark style="color:purple;">WriteFunctionArg</mark>

Module write function argument.

```typescript
{
  name: string; // arg's name 
  description: string; // arg's description
  type: string; // arg's solidity type, e.g. 'uint256'
  displayType: string; // a free-text field that tells front ends how to generate a proper UI component for the parameter
  optional?: boolean; // setting to 'true' indicates that this input is optional
}
```

### <mark style="color:purple;">ModuleCreationArgs</mark>

The arguments that are passed to the module [factory's creation function](create-new-instance-s.md#createnewinstance). The arguments are divided into two arrays: `immutable` and `mutable`. The `immutable` array contains arguments that are set once when the module instance is created and cannot be changed. The `mutable` array contains arguments that can be changed after the module instance is created.

* `useHatId` - By default, new instances should be created with the `hatId` value set to the target hat's ID.  A `false` value here indicates that the module's `hatId` value should be set to zero.
* In both the `immutable` and `mutable` array properties, the order of the arguments must match the order expected by the contract.

```typescript
{
  useHatId: boolean; 
  immutable: ModuleCreationArg[];
  mutable: ModuleCreationArg[];
}
```

### <mark style="color:purple;">ModuleCreationArg</mark>

Immutable/mutable argument, provided in the module's [creation arguments](types.md#modulecreationargs).

```typescript
{
  name: string; // arg's name
  description: string; // arg's description
  type: string; // arg's solidity type, e.g. 'uint256'
  example: unknown; // example value 
  displayType: string; // a free-text field that tells front ends how to generate a proper UI component for the parameter
}
```



### <mark style="color:purple;">Factory</mark>

A [HatsModuleFactory](../building-hats-modules/how-module-instances-are-deployed.md) metadata object.

```typescript
{
  name: string;
  details: string;
  links: {
    label: string;
    link: string;
  }[];
  implementationAddress: string;
  deployments: {
    chainId: string;
    block: string;
  }[];
  abi: Abi;
}
```

### <mark style="color:purple;">Registry</mark>

A [Hats Modules Registry](../building-hats-modules/modules-registry.md) object.

```typescript
{
  factory: Factory;
  eligibilitiesChain: ChainModule;
  togglesChain: ChainModule;
  modules: Module[];
}
```

### <mark style="color:purple;">ModuleParameter</mark>

Module parameter object, as returned by the [getInstanceParameters](interact-with-instances.md#getinstanceparameters) function.

```typescript
{
  label: string;
  value: unknown;
  solidityType: string;
  displayType: string;
}
```

### <mark style="color:purple;">ArgumentTsType</mark>

A Typescript type, as returned by the [solidityToTypescriptType function](utilities.md#soliditytotypescripttype).

```typescript
| "number"
| "bigint"
| "string"
| "boolean"
| "number[]"
| "bigint[]"
| "string[]"
| "boolean[]"
| "unknown";
```
