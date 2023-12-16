# Creating New Instances

Create new Instances of Hats Signer Gate (HSG) and/or Multi Hats Signer Gate (MHSG), optionally together with a new Safe, using the [Hats Signer Gate Factory](https://github.com/Hats-Protocol/hats-zodiac/blob/main/src/HatsSignerGateFactory.sol).&#x20;

### <mark style="color:purple;">deployHatsSignerGateAndSafe</mark>

Create a new HSG and a new Safe, all wired up together.

```typescript
const createHsgResult = await hatsSignerGateClient.deployHatsSignerGateAndSafe({
    account,
    ownerHatId,
    signersHatId,
    minThreshold,
    targetThreshold,
    maxSigners,
});
```

_**Arguments**_:

```typescript
{
    account: Account | Address;
    ownerHatId: bigint;
    signersHatId: bigint;
    minThreshold: bigint;
    targetThreshold: bigint;
    maxSigners: bigint;
}
```

* `account` - Viem account (Address for JSON-RPC accounts or Account for other types).
* `ownerHatId` - ID of the HSG's Owner Hat.
* `signersHatId` - ID of the HSG's Signers Hat.
* `minThreshold` - HSG's min threshold.
* `targetThreshold` - HSG's target threshold.
* `maxSigners` - HSG's max amount of signers.

_**Response**_:

```typescript
{
  status: "success" | "reverted";
  transactionHash: `0x${string}`;
  newHsgInstance: `0x${string}`;
  newSafeInstance: `0x${string}`;
}
```

* `status` - "success" if transaction was successful, "reverted" if transaction reverted.
* `transactionHash` - transaction's hash.
* `newHsgInstance` - In case of success, the address of the new HSG instance.
* newSafeInstance - In case of success, the address of the new Safe instance.

### <mark style="color:purple;">deployHatsSignerGate</mark>

Deploy a new HSG and relate it to an existing Safe. In order to wire it up to the existing Safe, the owners of the Safe must enable it as a module and guard.

* WARNING: HatsSignerGate must not be attached to a Safe with any other modules.
* WARNING: HatsSignerGate must not be attached to its Safe if `validSignerCount() >= _maxSigners`

Before wiring up HatsSignerGate to its Safe, call `canAttachHSGToSafe` and make sure the result is `true`. Failure to do so may result in the Safe being locked forever.

```typescript
const createHsgResult = await hatsSignerGateClient.deployHatsSignerGate({
    account,
    ownerHatId,
    signersHatId,
    safe,
    minThreshold,
    targetThreshold,
    maxSigners,
});
```

_**Arguments**_:

```typescript
{
    account: Account | Address;
    ownerHatId: bigint;
    signersHatId: bigint;
    safe: Address;
    minThreshold: bigint;
    targetThreshold: bigint;
    maxSigners: bigint;
}
```

* `account` - Viem account (Address for JSON-RPC accounts or Account for other types).
* `ownerHatId` - ID of the HSG's Owner Hat.
* `signersHatId` - ID of the HSG's Signers Hat.
* `safe` - Existing Gnosis Safe that the signers will join.
* `minThreshold` - HSG's min threshold.
* `targetThreshold` - HSG's target threshold.
* `maxSigners` - HSG's max amount of signers.

_**Response**_:

```typescript
{
  status: "success" | "reverted";
  transactionHash: `0x${string}`;
  newHsgInstance: `0x${string}`;
}
```

* `status` - "success" if transaction was successful, "reverted" if transaction reverted.
* `transactionHash` - transaction's hash.
* `newHsgInstance` - In case of success, the address of the new HSG instance.

### <mark style="color:purple;">deployMultiHatsSignerGateAndSafe</mark>

Create a new MHSG and a new Safe, all wired up together.

```typescript
const createMhsgResult = await hatsSignerGateClient.deployMultiHatsSignerGateAndSafe({
    account,
    ownerHatId,
    signersHatIds,
    minThreshold,
    targetThreshold,
    maxSigners,
});
```

_**Arguments**_:

```typescript
{
    account: Account | Address;
    ownerHatId: bigint;
    signersHatIds: bigint[];
    minThreshold: bigint;
    targetThreshold: bigint;
    maxSigners: bigint;
}
```

* `account` - Viem account (Address for JSON-RPC accounts or Account for other types).
* `ownerHatId` - ID of the MHSG's Owner Hat.
* `signersHatIds` - IDs of the MHSG's Signers Hats.
* `minThreshold` - MHSG's min threshold.
* `targetThreshold` - MHSG's target threshold.
* `maxSigners` - MHSG's max amount of signers.

_**Response**_:

```typescript
{
  status: "success" | "reverted";
  transactionHash: `0x${string}`;
  newMultiHsgInstance: `0x${string}`;
  newSafeInstance: `0x${string}`;
}
```

* `status` - "success" if transaction was successful, "reverted" if transaction reverted.
* `transactionHash` - transaction's hash.
* `newMultiHsgInstance` - In case of success, the address of the new MHSG instance.
* newSafeInstance - In case of success, the address of the new Safe instance.

### <mark style="color:purple;">deployMultiHatsSignerGate</mark>

Deploy a new MHSG and relate it to an existing Safe. In order to wire it up to the existing Safe, the owners of the Safe must enable it as a module and guard.

* WARNING: MultiHatsSignerGate must not be attached to a Safe with any other modules.
* WARNING: MultiHatsSignerGate must not be attached to its Safe if `validSignerCount()` >= `_maxSigners`

Before wiring up MultiHatsSignerGate to its Safe, call `canAttachMHSGToSafe` and make sure the result is `true`. Failure to do so may result in the Safe being locked forever.

```typescript
const createMhsgResult = await hatsSignerGateClient.deployMultiHatsSignerGate({
    account,
    ownerHatId,
    signersHatIds,
    safe,
    minThreshold,
    targetThreshold,
    maxSigners,
});
```

_**Arguments**_:

```typescript
{
    account: Account | Address;
    ownerHatId: bigint;
    signersHatIds: bigint[];
    safe: Address;
    minThreshold: bigint;
    targetThreshold: bigint;
    maxSigners: bigint;
}
```

* `account` - Viem account (Address for JSON-RPC accounts or Account for other types).
* `ownerHatId` - ID of the MHSG's Owner Hat.
* `signersHatIds` - IDs of the MHSG's Signers Hats.
* `safe` - Existing Gnosis Safe that the signers will join.
* `minThreshold` - MHSG's min threshold.
* `targetThreshold` - MHSG's target threshold.
* `maxSigners` - MHSG's max amount of signers.

_**Response**_:

```typescript
{
  status: "success" | "reverted";
  transactionHash: `0x${string}`;
  newMultiHsgInstance: `0x${string}`;
}
```

* `status` - "success" if transaction was successful, "reverted" if transaction reverted.
* `transactionHash` - transaction's hash.
* `newMultiHsgInstance` - In case of success, the address of the new MHSG instance.
