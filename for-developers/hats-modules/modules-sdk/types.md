# Types

### <mark style="color:purple;">Module</mark>

Represents a module object, compatible with the registry's module objects.

```typescript
{
  name: string;
  details: string[];
  links: {
    label: string;
    link: string;
  }[];
  parameters: {
    label: string;
    functionName: string;
    displayType: string;
  }[];
  type: {
    eligibility: boolean;
    toggle: boolean;
    hatter: boolean;
  };
  implementationAddress: string;
  deployments: {
    chainId: string;
    block: string;
  }[];
  creationArgs: ModuleCreationArgs;
  abi: Abi;
}
```

### <mark style="color:purple;">Factory</mark>

Represents a [HatsModuleFactory](../building-hats-modules/how-module-instances-are-deployed.md) object.

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

Represents a [Hats Modules Registry](../building-hats-modules/modules-registry.md) object.

```typescript
{
  factory: Factory;
  eligibilitiesChain: ChainModule;
  togglesChain: ChainModule;
  modules: Module[];
}
```

### <mark style="color:purple;">ModuleParameter</mark>

Represents a module parameter object, as returned by the [getInstanceParameters](interact-with-instances.md#getinstanceparameters) function.

```typescript
{
  label: string;
  value: unknown;
  solidityType: string;
  displayType: string;
}
```

### <mark style="color:purple;">ModuleCreationArg</mark>

Represents an immutable/mutable argument, as provided in Module objects.

```typescript
{
  name: string;
  description: string;
  type: string;
  example: unknown;
  displayType: string;
}
```

### <mark style="color:purple;">ModuleCreationArgs</mark>

Represents the Module creation arguments, as provided in Module objects.&#x20;

```typescript
{
  useHatId: boolean;
  immutable: ModuleCreationArg[];
  mutable: ModuleCreationArg[];
}
```

### <mark style="color:purple;">ArgumentTsType</mark>

Represents a Typescript type, as returned by the [solidityToTypescriptType function](utilities.md#soliditytotypescripttype).

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
