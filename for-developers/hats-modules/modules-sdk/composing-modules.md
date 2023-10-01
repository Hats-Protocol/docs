# Composing Modules

The following functions create new Eligibility/Toggle modules that compose other existing modules with "and"/"or" logical operations. Check out the documentation [here](../../building-hats-modules/about-module-chains.md) to learn more.

### <mark style="color:purple;">createEligibilitiesChain</mark>

Create a new eligibilities chain module.&#x20;

```typescript
const createInstanceResult = await hatsModulesClient.createEligibilitiesChain({
    account,
    hatId,
    numClauses,
    clausesLengths,
    modules
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
}
```

* `account` - Viem account (Address for JSON-RPC accounts or Account for other types).
* `hatId` - The hat ID for which the module is created.
* `numClauses` - Number of conjunction clauses.
* `clausesLengths` - Length of each clause.
* `modules`- Array of module instances to chain, at the order corresponding to the provided clauses.

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
    modules
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
}
```

* `account` - Viem account (Address for JSON-RPC accounts or Account for other types).
* `hatId` - The hat ID for which the module is created.
* `numClauses` - Number of conjunction clauses.
* `clausesLengths` - Length of each clause.
* `modules`- Array of module instances to chain, at the order corresponding to the provided clauses.

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
