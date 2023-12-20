# HSG & MHSG Handlers

The following section describes a different way of interacting with HSG and MHSG instances, than documented in the previous sections. In particular, in the previous sections, for each operation on the [HSG](hats-signer-gate.md) and [MHSG](multi-hats-signer-gate.md) contracts, there's a matching function in the SDK. &#x20;

In addition to these individual functions, the SDK also includes a single handler for calling the write operations of both HSG and MHSG instances. This enables HSG/MHSG interactions to be optionally handled in a similar way to [Hats Modules interactions](../hats-modules/modules-sdk/interact-with-instances.md#callinstancewritefunction), by working with the HSG and MHSG [metadata objects](hsg-and-mhsg-handlers.md#metadata) and the single write functions [handler](hsg-and-mhsg-handlers.md#handler).

## Handlers

### <mark style="color:purple;">callInstanceWriteFunction</mark>

Call a HSG/MHSG instance's write function.

```typescript
const res = await hatsSignerGateClient.callInstanceWriteFunction({
    account,
    type,
    instance,
    func,
    args,
});
```

_**Arguments**_:

```typescript
{
    account: Account | Address;
    type: HsgType;
    instance: Address;
    func: WriteFunction;
    args: unknown[];
}
```

* `account` - Viem account (Address for JSON-RPC accounts or Account for other types).
* `type` - 'HSG' or 'MHSG'.
* `instance` - The MHSG/HSG instance address.
* `func` - The write function to call, provided as an object of type [WriteFunction](hsg-and-mhsg-handlers.md#writefunction).
* `args` - The arguments with which to call the function, as objects of type [WriteFunctionArg](hsg-and-mhsg-handlers.md#writefunctionarg).

_**Response**_:

```typescript
{
  status: "success" | "reverted";
  transactionHash: `0x${string}`;
}
```

* `status` - "success" if transaction was successful, "reverted" if transaction reverted.
* `transactionHash` - transaction's hash.

### <mark style="color:purple;">getInstanceParameters</mark>

Get a HSG or MHSG instance live parameters:

* Safe address
* Min threshold
* Target threshold
* Max signers
* Owner Hat

```typescript
const params = await hatsSignerGateClient.getInstanceParameters(instance);
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
* `displayType`- The parameter's display type. Its purpose is for UIs to be able to render an appropriate component for the parameter

## Metadata

Both the HSG and MHSG metadata objects include their ABIs, all their [write functions](hsg-and-mhsg-handlers.md#writefunction) together with the metadata of each function and the [custom roles](hsg-and-mhsg-handlers.md#role) that are associated with them.&#x20;

### <mark style="color:purple;">getMetadata</mark>

Get the metadata object of HSG or MHSG.

```typescript
const metadata = await hatsSignerGateClient.getMetadata(type);
```

_**Arguments**_:

```typescript
HsgType
```

"HSG" or "MHSG"

_**Response**_:

```typescript
HsgMetadata
```

An object of type [HsgMetadata](hsg-and-mhsg-handlers.md#hsgmetadata).

## Types

### <mark style="color:purple;">HsgMetadata</mark>

Represents a HSG or MHSG metadata object.

```typescript
{
  customRoles: Role[]; // HSG/MHSG custom roles
  writeFunctions: WriteFunction[]; // HSG/MHSG write functions
  abi: Abi; // HSG/MHSG ABI
}
```

### <mark style="color:purple;">Role</mark>

A  custom HSG/MHSG role. Each role is associated with a hat and grants permissions to the hat's wearer(s) to call certain functions on the contract.

There are two special roles with a reserved ID:

1. `public` role, associated with functions that are permitted to any caller.
2. `hatAdmins` role, associated with functions that are permitted to the target hat's admins.

```typescript
{
  id: string; // role's ID
  name: string; // role's name
  criteria: string; // The name of the contract function which can be used to retrieve the role's hat
  hatAdminsFallback?: boolean; // 'true' indicates that the role is granted to the target hat's admin(s) if/when the role's criteria function returns zero.
}
```

### <mark style="color:purple;">WriteFunction</mark>

The HSG/MHSG write functions. Each write function is associated with a role that grants permissions to the role's wearer(s) to call the function on the contract.

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

HSG/MHSG write function argument.

```typescript
{
  name: string; // arg's name
  description: string; // arg's description
  type: string; // arg's solidity type, e.g. 'uint256'
  displayType: string; // a free-text field that tells front ends how to generate a proper UI component for the parameter
  optional?: boolean; // setting to 'true' indicates that this input is optional
}
```
