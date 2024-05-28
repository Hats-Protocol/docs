# Composing Modules

The following functions support the usage Eligibility/Toggle modules that compose other existing modules with "and"/"or" logical operations. Check out the documentation [here](../../building-hats-modules/about-module-chains.md) to learn more.

### Create New Eligibility/Toggle Chains

### <mark style="color:purple;">createEligibilitiesChain</mark>

Create a new eligibilities chain module.&#x20;

```typescript
const createInstanceResult = await hatsModulesClient.createEligibilitiesChain({
    account,
    hatId,
    numClauses,
    clausesLengths,
    modules,
    saltNonce,
});
```

_**Arguments**_:

```typescript
{
    account: Account | Address;
    hatId: bigint;
    numClauses: number;
    clausesLengths: number[];
    modules: `0x${string}`[];
    saltNonce?: bigint;
}
```

* `account` - Viem account (Address for JSON-RPC accounts or Account for other types).
* `hatId` - The hat ID for which the module is created.
* `numClauses` - Number of conjunction clauses.
* `clausesLengths` - Length of each clause.
* `modules`- Array of module instances to chain, at the order corresponding to the provided clauses.
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
* `newInstance` - In case of success, the address of the new chain module instance.

### <mark style="color:purple;">createTogglesChain</mark>

Create a new toggles chain module.

```typescript
const createInstanceResult = await hatsModulesClient.createTogglesChain({
    account,
    hatId,
    numClauses,
    clausesLengths,
    modules,
    saltNonce,
});
```

_**Arguments**_:

```typescript
{
    account: Account | Address;
    hatId: bigint;
    numClauses: number;
    clausesLengths: number[];
    modules: `0x${string}`[];
    saltNonce?: bigint;
}
```

* `account` - Viem account (Address for JSON-RPC accounts or Account for other types).
* `hatId` - The hat ID for which the module is created.
* `numClauses` - Number of conjunction clauses.
* `clausesLengths` - Length of each clause.
* `modules`- Array of module instances to chain, at the order corresponding to the provided clauses.
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
* `newInstance` - In case of success, the address of the new chain module instance.

### Read From Eligibility/Toggle Chains

The following functions support reading from chain module instances.&#x20;

### <mark style="color:purple;">getRulesets</mark>

Get the rulesets of a module instance.

A ruleset is an array of modules which are chained together with an "AND" logical operator. If the module is a chain with multiple rulesets, then these rulesets are chained together with an "OR" logical operator.

If the provided address is a single module instance (not a chain), then the result will be a single ruleset, which will consist of the single module instance.

```typescript
const rulesets = await hatsModulesClient.getRulesets(address);
```

_**Arguments**_:

```typescript
`0x${string}`
```

Instance address.

_**Response**_:

```typescript
Ruleset[] | undefined
```

The module's [rulesets](types.md#ruleset), or `undefined` if the provided address is not a module.

### <mark style="color:purple;">getRulesetsBatched</mark>

Get the rulesets of multiple module instances.

A ruleset is an array of modules which are chained together with an "AND" logical operator. If the module is a chain with multiple rulesets, then these rulesets are chained together with an "OR" logical operator.

If the provided address is a single module instance (not a chain), then the result will be a single ruleset, which will consist of the single module instance.

```typescript
const rulesets = await hatsModulesClient.getRulesetsBatched(addresses);
```

_**Arguments**_:

```typescript
`0x${string}`[]
```

Array of instance addresses.

_**Response**_:

```typescript
(Ruleset[] | undefined)[]
```

For each module instance, returns the module's [rulesets](types.md#ruleset), or `undefined` if the provided address is not a module.

### <mark style="color:purple;">isChain</mark>

Check whether a module instance is a modules chain.

```typescript
const isChain = await hatsModulesClient.isChain(address);
```

_**Arguments**_:

```typescript
`0x${string}`
```

Instance address.

_**Response**_:

```typescript
boolean
```

`true` if the instance is a chain, `false` otherwise.

### <mark style="color:purple;">isChainBatched</mark>

Check whether multiple module instances are modules chains.

```typescript
const isChainBatched = await hatsModulesClient.isChainBatched(addresses);
```

_**Arguments**_:

```typescript
`0x${string}`[]
```

Instance addresses.

_**Response**_:

```typescript
boolean[]
```

For each instance, `true` if the instance is a chain, `false` otherwise.
