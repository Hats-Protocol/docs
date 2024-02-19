# Types

### <mark style="color:purple;">Operation</mark>

Execution data for a Hats Account operation.

```typescript
{
  to: Address;
  value: bigint;
  data: Hex;
  operation: OperationType;
}
```

* to - The target address of the operation.
* value - The Ether value to be sent to the target.
* data - The encoded operation calldata.
* operation - A value of type [OperationType](types.md#operationtype), indicating the type of operation to perform (call or delegate-call).

### <mark style="color:purple;">OperationType</mark>

Enum describing the operation to execute.

```typescript
enum OperationType {
  Call,
  DelegateCall,
}
```

### <mark style="color:purple;">CreateAccountResult</mark>

Account creation result.

```typescript
enum OperationType {
  status: "success" | "reverted";
  transactionHash: Address;
  newAccount: Address;
}
```

### <mark style="color:purple;">ExecutionResult</mark>

Hats Account execution result.

```typescript
enum OperationType {
  status: "success" | "reverted";
  transactionHash: Address;
}
```
