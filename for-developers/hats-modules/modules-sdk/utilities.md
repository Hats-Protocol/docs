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
