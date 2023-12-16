# Hats Signer Gate

Interact with [HSG](https://github.com/Hats-Protocol/hats-zodiac/blob/main/src/HatsSignerGate.sol) instances.

## Signers Management

### <mark style="color:purple;">hsgClaimSigner</mark>

Claim signer rights on the safe.&#x20;

In order to successfully claim:

* The calling account must wear the [Signers Hat](hats-signer-gate.md#hsgsignershatid). Use [this](hats-signer-gate.md#hsgisvalidsigner) function is order to check whether an account is a valid signer.
* Caller must not be already a signer.
* The current amount of valid signers should be smaller than the configured amount of maximum signers.

```typescript
const claimSignerResult = await hatsSignerGateClient.hsgClaimSigner({
    account,
    hsgInstance,
});
```

_**Arguments**_:

```typescript
{
    account: Account | Address;
    hsgInstance: Address;
}
```

* `account` - Viem account (Address for JSON-RPC accounts or Account for other types).
* `hsgInstance` - HSG's instance address.

_**Response**_:

```typescript
{
  status: "success" | "reverted";
  transactionHash: `0x${string}`;
}
```

* `status` - "success" if transaction was successful, "reverted" if transaction reverted.
* `transactionHash` - transaction's hash.

### <mark style="color:purple;">hsgIsValidSigner</mark>

Check if an account is wearing the Signers Hat (regardless whether the account has claimed signer rights or not).

<pre class="language-typescript"><code class="lang-typescript">const isValid = await hatsSignerGateClient.hsgIsValidSigner({
<strong>    hsgInstance,
</strong><strong>    address    
</strong>});
</code></pre>

_**Arguments**_:

```typescript
{
    hsgInstance: Address;
    address: Address;
}
```

* `hsgInstance` - HSG's instance address.
* `address` -The address to check.

_**Response**_:

```typescript
boolean
```

`true` if valid, `false` otherwise.

### <mark style="color:purple;">validSignerCount</mark>

Tallies the number of existing Safe owners that wear the Signers Hat.

<pre class="language-typescript"><code class="lang-typescript">const count = await hatsSignerGateClient.validSignerCount({
<strong>    instance 
</strong>});
</code></pre>

_**Arguments**_:

```typescript
{
    instance: Address;
}
```

* `instance` - HSG's instance address.

_**Response**_:

```typescript
bigint
```

The number of valid signers on the Safe.

### <mark style="color:purple;">reconcileSignerCount</mark>

Tallies the number of existing Safe owners that wear a Signers Hat and updates the Safe's threshold if necessary. Does NOT remove invalid Safe owners.

```typescript
const res = await hatsSignerGateClient.reconcileSignerCount({
    account,
    instance,
});
```

_**Arguments**_:

```typescript
{
    account: Account | Address;
    instance: Address;
}
```

* `account` - Viem account (Address for JSON-RPC accounts or Account for other types).
* `instance` - HSG's instance address.

_**Response**_:

```typescript
{
  status: "success" | "reverted";
  transactionHash: `0x${string}`;
}
```

* `status` - "success" if transaction was successful, "reverted" if transaction reverted.
* `transactionHash` - transaction's hash.

### <mark style="color:purple;">removeSigner</mark>

Removes an invalid signer from the Safe, updating its threshold if appropriate.

```typescript
const res = await hatsSignerGateClient.removeSigner({
    account,
    instance,
    signer,
});
```

_**Arguments**_:

```typescript
{
    account: Account | Address;
    instance: Address;
    signer: Address;
}
```

* `account` - Viem account (Address for JSON-RPC accounts or Account for other types).
* `instance` - HSG's instance address.
* `signer` - The address to remove if not a valid signer.

_**Response**_:

```typescript
{
  status: "success" | "reverted";
  transactionHash: `0x${string}`;
}
```

* `status` - "success" if transaction was successful, "reverted" if transaction reverted.
* `transactionHash` - transaction's hash.

## HSG Instance Properties

Getters for the basic properties of a HSG instance.

### <mark style="color:purple;">hsgSignersHatId</mark>

Get a HSG's Signers Hat ID.

<pre class="language-typescript"><code class="lang-typescript">const signersHat = await hatsSignerGateClient.hsgSignersHatId({
<strong>    hsgInstance 
</strong>});
</code></pre>

_**Arguments**_:

```typescript
{
    hsgInstance: Address;
}
```

* `hsgInstance` - HSG's instance address.

_**Response**_:

```typescript
bigint
```

HSG's Signers Hat ID.

### <mark style="color:purple;">getSafe</mark>

Get a HSG's attached Safe.

<pre class="language-typescript"><code class="lang-typescript">const safe = await hatsSignerGateClient.getSafe({
<strong>    instance 
</strong>});
</code></pre>

_**Arguments**_:

```typescript
{
    instance: Address;
}
```

* `instance` - HSG's instance address.

_**Response**_:

```typescript
Address
```

Address of the attached Safe.

### <mark style="color:purple;">getMinThreshold</mark>

Get a HSG's minimum threshold.

<pre class="language-typescript"><code class="lang-typescript">const minThreshold = await hatsSignerGateClient.getMinThresholde({
<strong>    instance 
</strong>});
</code></pre>

_**Arguments**_:

```typescript
{
    instance: Address;
}
```

* `instance` - HSG's instance address.

_**Response**_:

```typescript
bigint
```

The instance's min threshold.

### <mark style="color:purple;">getTargetThreshold</mark>

Get a HSG's target threshold.

<pre class="language-typescript"><code class="lang-typescript">const targetThreshold = await hatsSignerGateClient.getTargetThreshold({
<strong>    instance 
</strong>});
</code></pre>

_**Arguments**_:

```typescript
{
    instance: Address;
}
```

* `instance` - HSG's instance address.

_**Response**_:

```typescript
bigint
```

The instance's target threshold.

### <mark style="color:purple;">getMaxSigners</mark>

Get a HSG's maximum amount of signers.

<pre class="language-typescript"><code class="lang-typescript">const maxSigners = await hatsSignerGateClient.getMaxSigners({
<strong>    instance 
</strong>});
</code></pre>

_**Arguments**_:

```typescript
{
    instance: Address;
}
```

* `instance` - HSG's instance address.

_**Response**_:

```typescript
bigint
```

The instance's max signers.

### <mark style="color:purple;">getOwnerHat</mark>

Get a HSG's Owner Hat.

<pre class="language-typescript"><code class="lang-typescript">const ownerHat = await hatsSignerGateClient.getOwnerHat({
<strong>    instance 
</strong>});
</code></pre>

_**Arguments**_:

```typescript
{
    instance: Address;
}
```

* `instance` - HSG's instance address.

_**Response**_:

```typescript
bigint
```

The instance's Owner Hat.

## HSG Owner

Following functions are only authorized to the wearer(s) of the HSG instance's Owner Hat.

### <mark style="color:purple;">setTargetThreshold</mark>

Sets a new target threshold, and changes Safe's threshold if appropriate.&#x20;

In order to successfully execute the function:

* The caller must be a wearer of the HSG's Owner Hat.
* The new target threshold should not be smaller than the minimum threshold.
* The new target threshold should not be larger than the maximum amount of signers.

```typescript
const res = await hatsSignerGateClient.setTargetThreshold({
    account,
    instance,
    targetThreshold,
});
```

_**Arguments**_:

```typescript
{
    account: Account | Address;
    instance: Address;
    targetThreshold: bigint;
}
```

* `account` - Viem account (Address for JSON-RPC accounts or Account for other types).
* `instance` - HSG's instance address.
* `targetThreshold` - The new target threshold to set.

_**Response**_:

```typescript
{
  status: "success" | "reverted";
  transactionHash: `0x${string}`;
}
```

* `status` - "success" if transaction was successful, "reverted" if transaction reverted.
* `transactionHash` - transaction's hash.

### <mark style="color:purple;">setMinThreshold</mark>

Sets a new minimum threshold.

In order to successfully execute the function:

* The caller must be a wearer of the HSG's Owner Hat.
* The new minimum threshold should not be larger than the target threshold.
* The new minimum threshold should not be larger than the maximum amount of signers.

```typescript
const res = await hatsSignerGateClient.setMinThreshold({
    account,
    instance,
    minThreshold,
});
```

_**Arguments**_:

```typescript
{
    account: Account | Address;
    instance: Address;
    minThreshold: bigint;
}
```

* `account` - Viem account (Address for JSON-RPC accounts or Account for other types).
* `instance` - HSG's instance address.
* `minThreshold` - The new minimum threshold to set.

_**Response**_:

```typescript
{
  status: "success" | "reverted";
  transactionHash: `0x${string}`;
}
```

* `status` - "success" if transaction was successful, "reverted" if transaction reverted.
* `transactionHash` - transaction's hash.

### <mark style="color:purple;">setOwnerHat</mark>

Sets a new Owner Hat.

In order to successfully execute the function:

* The caller must be a wearer of the current Owner Hat.

```typescript
const res = await hatsSignerGateClient.setOwnerHat({
    account,
    instance,
    newOwnerHat,
    hatsContractAddress,
});
```

_**Arguments**_:

```typescript
{
    account: Account | Address;
    instance: Address;
    newOwnerHat: bigint;
    hatsContractAddress: Address;
}
```

* `account` - Viem account (Address for JSON-RPC accounts or Account for other types).
* `instance` - HSG's instance address.
* `newOwnerHat` - The new Owner Hat to set.
* `hatsContractAddress` - The Hats.sol contract address of the new Owner Hat.

_**Response**_:

```typescript
{
  status: "success" | "reverted";
  transactionHash: `0x${string}`;
}
```

* `status` - "success" if transaction was successful, "reverted" if transaction reverted.
* `transactionHash` - transaction's hash.
