# Utilities

### <mark style="color:purple;">getSchema</mark>

The SDK uses Zod schemas in order to verify inputs for [createNewInstance](broken-reference), according to their target Solidity types. The `getSchema` function is exported as a utility function, to get the Zod schema for a corresponding Solidity type.

```typescript
import { getSchema } from "@hatsprotocol/modules-sdk";

const schema = getSchema(solidityType);
```

_**Arguments**_:

```typescript
solidityType: string
```

`solidityType` - The name of the Solidity type, e.g. "uint256".

_**Response**_:

```typescript
ZodType
```

The Zod schema for the provided type.&#x20;

### <mark style="color:purple;">verify</mark>

Verify a value according to its target Solidity type.

```typescript
import { verify } from "@hatsprotocol/modules-sdk";

const isValid = verify(val, type);
```

_**Arguments**_:

```typescript
(val: unknown, type: string)
```

* `val` - The value to verify.
* `type` - The target Solidity type for the provided value.

_**Response**_:

```typescript
boolean
```

`true` if the provided value is compatible with the Solidity type, `false` otherwise.

### <mark style="color:purple;">solidityToTypescriptType</mark>

Utility function that maps between a Solidity type to its compatible Typescript type.

```typescript
import { solidityToTypescriptType } from "@hatsprotocol/modules-sdk";

const tsType = solidityToTypescriptType(solidityType);
```

_**Arguments**_:

```typescript
solidityType: string
```

`solidityType` - The name of the Solidity type, e.g. "uint256".

_**Response**_:

```typescript
"number"    | 
"bigint"    |
"string"    |
"boolean"   |
"number[]"  | 
"bigint[]"  | 
"string[]"  | 
"boolean[]" | 
"unknown"
```

The name of the Typescript type which is compatible to the provided Solidity one.

### <mark style="color:purple;">checkAndEncodeArgs</mark>

Check and encode the immutable and mutable arguments for module creation.

This is a utility function for interacting with the [HatsModuleFactory](../building-hats-modules/how-module-instances-are-deployed.md) directly, rather than using the [createNewInstance](create-new-instance-s.md#createnewinstance) function from the SDK. This may be useful in cases where the module creation is proxied by another contract and expects similar input parameters as the [createHatsModule](https://github.com/Hats-Protocol/hats-module/blob/38f80eed6ce444f924f5982858daf75e724be6f9/src/HatsModuleFactory.sol#L69C12-L69C28) function from the factory.

```typescript
import { checkAndEncodeArgs } from "@hatsprotocol/modules-sdk";

const { encodedImmutableArgs, encodedMutableArgs } = checkAndEncodeArgs({
   module,
   immutableArgs,
   mutableArgs,
});
```

_**Arguments**_:

```typescript
{
  module: Module;
  immutableArgs: unknown[];
  mutableArgs: unknown[];
}
```

`module` - The module object of the module that will be created.

`immutableArgs` - The module's immutable arguments.

`mutableArgs` - The modules's mutable arguments.

_**Response**_:

```typescript
{
  encodedImmutableArgs: "" | `0x${string}`;
  encodedMutableArgs: "" | `0x${string}`;
}
```

The encoded immutable and mutable arguments, as expected by the [createHatsModule](https://github.com/Hats-Protocol/hats-module/blob/38f80eed6ce444f924f5982858daf75e724be6f9/src/HatsModuleFactory.sol#L69C12-L69C28) function from the factory.&#x20;

### <mark style="color:purple;">checkImmutableArgs</mark>

Check the immutable arguments for module creation.

Checks that the provided immutable arguments are valid according to the module's schema from the registry. If not, the function will throw a detailed error.

```typescript
import { checkImmutableArgs } from "@hatsprotocol/modules-sdk";

checkImmutableArgs({ module, immutableArgs });
```

_**Arguments**_:

```typescript
{
  module: Module;
  immutableArgs: unknown[];
}
```

`module` - The module object of the module that will be created.

`immutableArgs` - The module's immutable arguments.

### <mark style="color:purple;">checkMutableArgs</mark>

Check the mutable arguments for module creation.

Checks that the provided mutable arguments are valid according to the module's schema from the registry. If not, the function will throw a detailed error.

```typescript
import { checkMutableArgs } from "@hatsprotocol/modules-sdk";

checkMutableArgs({ module, mutableArgs });
```

_**Arguments**_:

```typescript
{
  module: Module;
  mutableArgs: unknown[];
}
```

`module` - The module object of the module that will be created.

`mutableArgs` - The module's mutable arguments.

### <mark style="color:purple;">getNewInstancesFromReceipt</mark>

Get the addresses of newly created module instance/s, using the creation transaction receipt.

```typescript
import { getNewInstancesFromReceipt } from "@hatsprotocol/modules-sdk";

const instances = getNewInstancesFromReceipt(receipt);
```

_**Arguments**_:

```typescript
receipt: TransactionReceipt
```

`receipt` - The transaction receipt as a TransactionReceipt Viem object.

_**Response**_:

```typescript
`0x${string}`[]
```

An array of the newly created instances/s.
