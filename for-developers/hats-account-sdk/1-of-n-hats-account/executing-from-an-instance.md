# Executing From An Instance

Execute operations from a Hats Account instance. Only wearers of the instance's hat can call the following functions.

### <mark style="color:purple;">execute</mark>

Execute an operation.

```typescript
const executionResult = await hatsAccount1ofNClient.execute({
    account,
    instance,
    operation,
});
```

_**Arguments**_:

```typescript
{
    account: Account | Address;
    instance: Address;
    operation: Operation;
}
```

* `account` - Viem account (Address for JSON-RPC accounts or Account for other types).
* `instance` - The Hats Account instance.
* `operation` - An object of type [Operation](types.md#operation), which includes the operation's execution data.

_**Response**_:

```typescript
{
  status: "success" | "reverted";
  transactionHash: `0x${string}`;
}
```

An object of type [ExecutionResult](types.md#executionresult), includes:

* `status` - "success" if transaction was successful, "reverted" if transaction reverted.
* `transactionHash` - transaction's hash.

### <mark style="color:purple;">executeBatch</mark>

Execute a batch of operations.

```typescript
const executionResult = await hatsAccount1ofNClient.executeBatch({
    account,
    instance,
    operations,
});
```

_**Arguments**_:

```typescript
{
    account: Account | Address;
    instance: Address;
    operations: Operation[];
}
```

* `account` - Viem account (Address for JSON-RPC accounts or Account for other types).
* `instance` - The Hats Account instance.
* `operations` - An array of  [Operation](types.md#operation) objects, each includes an operation's execution data.

_**Response**_:

```typescript
{
  status: "success" | "reverted";
  transactionHash: `0x${string}`;
}
```

An object of type [ExecutionResult](types.md#executionresult), includes:

* `status` - "success" if transaction was successful, "reverted" if transaction reverted.
* `transactionHash` - transaction's hash.
