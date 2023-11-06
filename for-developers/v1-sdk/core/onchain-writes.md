# Onchain Writes

### <mark style="color:purple;">mintTopHat</mark>

Create a new tophat (new tree).

```typescript
const mintTopHatResult = await hatsClient.mintTopHat({
    account,
    target,
    details,
    imageURI,
});
```

_**Arguments**_:

```typescript
{
    account: Account | Address;
    target: Address;
    details: string;
    imageURI?: string;
}
```

* `account` - Viem account (Address for JSON-RPC accounts or Account for other types).
* `target` - tophat's wearer address.
* `details` - tophat's details field.
* `imageURI` - optional tophat's image URI.

_**Response**_:

```typescript
{
  status: "success" | "reverted";
  transactionHash: `0x${string}`;
  hatId: bigint;
}
```

* `status` - "success" if transaction was successful, "reverted" if transaction reverted.
* `transactionHash` - transaction's hash.
* `hatId` - ID of the created tophat.

### <mark style="color:purple;">createHat</mark>

Create a hat.

```typescript
const createHatResult = await hatsClient.createHat({
    account,
    admin,
    details,
    maxSupply,
    eligibility,
    toggle,
    mutable,
    imageURI,
});
```

_**Arguments**_:

```typescript
{
    account: Account | Address;
    admin: bigint;
    details: string;
    maxSupply: number;
    eligibility: Address;
    toggle: Address;
    mutable: boolean;
    imageURI?: string;
}
```

* `account` - Viem account (Address for JSON-RPC accounts or Account for other types).
* `admin` - hat's admin ID.
* `details` - hat's details field.
* `maxSupply` - hat's maximum amount of possible wearers.
* `eligibility` - hat's eligibility address (zero address is not valid).
* `toggle` - hat's toggle address (zero address is not valid).
* `mutable` - true if the hat should be mutable, false otherwise.
* `imageURI` - optional hat's image URI.

_**Response**_:

```typescript
{
  status: "success" | "reverted";
  transactionHash: `0x${string}`;
  hatId: bigint;
}
```

* `status` - "success" if transaction was successful, "reverted" if transaction reverted.
* `transactionHash` - transaction's hash.
* `hatId` - ID of the created hat.

### <mark style="color:purple;">batchCreateHats</mark>

Create multiple hats.

```typescript
const batchCreateHatsResult = await hatsClient.batchCreateHats({
    account,
    admins,
    details,
    maxSupplies,
    eligibilityModules,
    toggleModules,
    mutables,
    imageURIs,
});
```

_**Arguments**_:

```typescript
{
    account: Account | Address;
    admins: bigint[];
    details: string[];
    maxSupplies: number[];
    eligibilityModules: Address[];
    toggleModules: Address[];
    mutables: boolean[];
    imageURIs?: string[];
}
```

* `account` - Viem account (Address for JSON-RPC accounts or Account for other types).
* `admins` - hats admin IDs.
* `details` - hats details fields.
* `maxSupplies` - hats maximum amounts of possible wearers.
* `eligibilityModules` - hats eligibility addresses (zero address is not valid).
* `toggleModules` - hats toggle addresses (zero address is not valid).
* `mutables` - true if the hat should be mutable, false otherwise.
* `imageURIs` - optional hats image URIs.

_**Response**_:

```typescript
{
  status: "success" | "reverted";
  transactionHash: `0x${string}`;
  hatIds: bigint[];
}
```

* `status` - "success" if transaction was successful, "reverted" if transaction reverted.
* `transactionHash` - transaction's hash.
* `hatIds` - IDs of the created hats.

### <mark style="color:purple;">mintHat</mark>

Mint a hat.

```typescript
const mintHatResult = await hatsClient.mintHat({
    account,
    hatId,
    wearer,
});
```

_**Arguments**_:

```typescript
{
    account: Account | Address;
    hatId: bigint;
    wearer: Address;
}
```

* `account` - Viem account (Address for JSON-RPC accounts or Account for other types).
* `hatId` - hat's ID.
* `wearer` - address of the new wearer.

_**Response**_:

```typescript
{
  status: "success" | "reverted";
  transactionHash: `0x${string}`;
}
```

* `status` - "success" if transaction was successful, "reverted" if transaction reverted.
* `transactionHash` - transaction's hash.

### <mark style="color:purple;">batchMintHats</mark>

Mint multiple hats.

```typescript
const batchMintHatsResult = await hatsClient.batchMintHats({
    account,
    hatIds,
    wearers,
});
```

_**Arguments**_:

```typescript
{
    account: Account | Address;
    hatIds: bigint[];
    wearers: Address[];
}
```

* `account` - Viem account (Address for JSON-RPC accounts or Account for other types).
* `hatIds` - hats IDs.
* `wearers` - addresses of the new wearers.

_**Response**_:

```typescript
{
  status: "success" | "reverted";
  transactionHash: `0x${string}`;
}
```

* `status` - "success" if transaction was successful, "reverted" if transaction reverted.
* `transactionHash` - transaction's hash.

### <mark style="color:purple;">setHatStatus</mark>

Set a hat's status to active/inactive.

```typescript
const setHatStatusResult = await hatsClient.setHatStatus({
    account,
    hatId,
    newStatus,
});
```

_**Arguments**_:

```typescript
{
    account: Account | Address;
    hatId: bigint;
    newStatus: boolean;
}
```

* `account` - Viem account (Address for JSON-RPC accounts or Account for other types).
* `hatId` - hat's ID.
* `newStatus` - hat's new status: `true` for active, `false` for inactive.

_**Response**_:

```typescript
{
  status: "success" | "reverted";
  transactionHash: `0x${string}`;
}
```

* `status` - "success" if transaction was successful, "reverted" if transaction reverted.
* `transactionHash` - transaction's hash.

### <mark style="color:purple;">checkHatStatus</mark>

Check a hat's status by calling its toggle module, and updating the status as needed.

```typescript
const checkHatStatusResult = await hatsClient.checkHatStatus({
    account,
    hatId,
});
```

_**Arguments**_:

```typescript
{
    account: Account | Address;
    hatId: bigint;
}
```

* `account` - Viem account (Address for JSON-RPC accounts or Account for other types).
* `hatId` - hat's ID.

_**Response**_:

```typescript
{
  status: "success" | "reverted";
  transactionHash: `0x${string}`;
  toggled: boolean;
  newStatus?: "active" | "inactive";
}
```

* `status` - "success" if transaction was successful, "reverted" if transaction reverted.
* `transactionHash` - transaction's hash.
* `toggled` - true if the hat's status was changed (toggled), false otherwise.
* `newStatus` - if hat's status was changed (toggled), then contains its new status.

### <mark style="color:purple;">setHatWearerStatus</mark>

Set a hat's wearer status.

```typescript
const setHatWearerStatusResult = await hatsClient.setHatWearerStatus({
    account,
    hatId,
    wearer,
    eligible,
    standing,
});
```

_**Arguments**_:

```typescript
{
    account: Account | Address;
    hatId: bigint;
    wearer: Address;
    eligible: boolean;
    standing: boolean;
}
```

* `account` - Viem account (Address for JSON-RPC accounts or Account for other types).
* `hatId` - hat's ID.
* `wearer` - wearer address.
* `eligible` - wearer's eligibility. `true` for eligible, `false` otherwise.
* `standing` - wearer's standing. `true` for good, `false` for bad.

_**Response**_:

```typescript
{
  status: "success" | "reverted";
  transactionHash: `0x${string}`;
}
```

* `status` - "success" if transaction was successful, "reverted" if transaction reverted.
* `transactionHash` - transaction's hash.

### <mark style="color:purple;">checkHatWearerStatus</mark>

Check a hat's wearer status by calling the hat's eligibility module. If the wearer is non eligible and/or in bad standing, then its hat is burned.

```typescript
const checkHatWearerStatusResult = await hatsClient.checkHatWearerStatus({
    account,
    hatId,
    wearer,
});
```

_**Arguments**_:

```typescript
{
    account: Account | Address;
    hatId: bigint;
    wearer: Address;
}
```

* `account` - Viem account (Address for JSON-RPC accounts or Account for other types).
* `hatId` - hat's ID.
* `wearer` - wearer address.

_**Response**_:

```typescript
{
  status: "success" | "reverted";
  transactionHash: `0x${string}`;
  wearerStandingUpdated: boolean;
  hatBurned: boolean;
  newWearerStanding?: "good" | "bad";
}
```

* `status` - "success" if transaction was successful, "reverted" if transaction reverted.
* `transactionHash` - Transaction's hash.
* `wearerStandingUpdated` - `true` if the wearer's standing was changed (toggled), `false` otherwise.
* `hatBurned` - `true` if the wearer's hat was burned in the transaction, `false` otherwise.
* `newWearerStanding` - if the wearer standing was changed, then contains the new standing status.

### <mark style="color:purple;">renounceHat</mark>

Renounce a hat. This action burns the hat for the renouncing wearer (the caller).

```typescript
const renounceHatResult = await hatsClient.renounceHat({
    account,
    hatId,
});
```

_**Arguments**_:

```typescript
{
    account: Account | Address;
    hatId: bigint;
}
```

* `account` - Viem account (Address for JSON-RPC accounts or Account for other types).
* `hatId` - hat's ID.

_**Response**_:

```typescript
{
  status: "success" | "reverted";
  transactionHash: `0x${string}`;
}
```

* `status` - "success" if transaction was successful, "reverted" if transaction reverted.
* `transactionHash` - transaction's hash.

### <mark style="color:purple;">transferHat</mark>

Transfer a hat from one wearer to another.

```typescript
const transferHatResult = await hatsClient.transferHat({
    account,
    hatId,
    from,
    to,
});
```

_**Arguments**_:

```typescript
{
    account: Account | Address;
    hatId: bigint;
    from: Address;
    to: Address;
}
```

* `account` - Viem account (Address for JSON-RPC accounts or Account for other types).
* `hatId` - hat's ID.
* `from` - current wearer address.
* `to` - new wearer address.

_**Response**_:

```typescript
{
  status: "success" | "reverted";
  transactionHash: `0x${string}`;
}
```

* `status` - "success" if transaction was successful, "reverted" if transaction reverted.
* `transactionHash` - transaction's hash.

### <mark style="color:purple;">makeHatImmutable</mark>

Make a hat immutable.

```typescript
const makeHatImmutableResult = await hatsClient.makeHatImmutable({
    account,
    hatId,
});
```

_**Arguments**_:

```typescript
{
    account: Account | Address;
    hatId: bigint;
}
```

* `account` - Viem account (Address for JSON-RPC accounts or Account for other types).
* `hatId` - hat's ID.

_**Response**_:

```typescript
{
  status: "success" | "reverted";
  transactionHash: `0x${string}`;
}
```

* `status` - "success" if transaction was successful, "reverted" if transaction reverted.
* `transactionHash` - transaction's hash.

### <mark style="color:purple;">changeHatDetails</mark>

Change a hat's details.

```typescript
const changeHatDetailsResult = await hatsClient.changeHatDetails({
    account,
    hatId,
    newDetails,
});
```

_**Arguments**_:

```typescript
{
    account: Account | Address;
    hatId: bigint;
    newDetails: string;
}
```

* `account` - Viem account (Address for JSON-RPC accounts or Account for other types).
* `hatId` - hat's ID.
* `newDetails` - hat's new details.

_**Response**_:

```typescript
{
  status: "success" | "reverted";
  transactionHash: `0x${string}`;
}
```

* `status` - "success" if transaction was successful, "reverted" if transaction reverted.
* `transactionHash` - transaction's hash.

### <mark style="color:purple;">changeHatEligibility</mark>

Change a hat's eligibility.

```typescript
const changeHatEligibilityResult = await hatsClient.changeHatEligibility({
    account,
    hatId,
    newEligibility,
});
```

_**Arguments**_:

```typescript
{
    account: Account | Address;
    hatId: bigint;
    newEligibility: Address;
}
```

* `account` - Viem account (Address for JSON-RPC accounts or Account for other types).
* `hatId` - hat's ID.
* `newEligibility` - hat's new eligibility.

_**Response**_:

```typescript
{
  status: "success" | "reverted";
  transactionHash: `0x${string}`;
}
```

* `status` - "success" if transaction was successful, "reverted" if transaction reverted.
* `transactionHash` - transaction's hash.

### <mark style="color:purple;">changeHatToggle</mark>

Change a hat's toggle.

```typescript
const changeHatToggleResult = await hatsClient.changeHatToggle({
    account,
    hatId,
    newToggle,
});
```

_**Arguments**_:

```typescript
{
    account: Account | Address;
    hatId: bigint;
    newToggle: Address;
}
```

* `account` - Viem account (Address for JSON-RPC accounts or Account for other types).
* `hatId` - hat's ID.
* `newToggle` - hat's new toggle.

_**Response**_:

```typescript
{
  status: "success" | "reverted";
  transactionHash: `0x${string}`;
}
```

* `status` - "success" if transaction was successful, "reverted" if transaction reverted.
* `transactionHash` - transaction's hash.

### <mark style="color:purple;">changeHatImageURI</mark>

Change a hat's image URI.

```typescript
const changeHatImageURIResult = await hatsClient.changeHatImageURI({
    account,
    hatId,
    newImageURI,
});
```

_**Arguments**_:

```typescript
{
    account: Account | Address;
    hatId: bigint;
    newImageURI: string;
}
```

* `account` - Viem account (Address for JSON-RPC accounts or Account for other types).
* `hatId` - hat's ID.
* `newImageURI` - hat's new image URI.

_**Response**_:

```typescript
{
  status: "success" | "reverted";
  transactionHash: `0x${string}`;
}
```

* `status` - "success" if transaction was successful, "reverted" if transaction reverted.
* `transactionHash` - transaction's hash.

### <mark style="color:purple;">changeHatMaxSupply</mark>

Change a hat's maximum supply.

```typescript
const changeHatMaxSupplyResult = await hatsClient.changeHatMaxSupply({
    account,
    hatId,
    newMaxSupply,
});
```

_**Arguments**_:

```typescript
{
    account: Account | Address;
    hatId: bigint;
    newMaxSupply: number;
}
```

* `account` - Viem account (Address for JSON-RPC accounts or Account for other types).
* `hatId` - hat's ID.
* `newMaxSupply` - hat's new maximum supply.

_**Response**_:

```typescript
{
  status: "success" | "reverted";
  transactionHash: `0x${string}`;
}
```

* `status` - "success" if transaction was successful, "reverted" if transaction reverted.
* `transactionHash` - transaction's hash.

### <mark style="color:purple;">requestLinkTopHatToTree</mark>

Request a link from a tophat to a new admin hat.

```typescript
const requestLinkTopHatToTreeResult = await hatsClient.requestLinkTopHatToTree({
    account,
    topHatDomain,
    requestedAdminHat,
});
```

_**Arguments**_:

```typescript
{
    account: Account | Address;
    topHatDomain: number;
    requestedAdminHat: bigint;
}
```

* `account` - Viem account (Address for JSON-RPC accounts or Account for other types).
* `topHatDomain` - the tree domain of the requesting tree. The tree domain is the first four bytes of the tophat ID.
* `requestedAdminHat` - ID of the requested new admin hat.

_**Response**_:

```typescript
{
  status: "success" | "reverted";
  transactionHash: `0x${string}`;
}
```

* `status` - "success" if transaction was successful, "reverted" if transaction reverted.
* `transactionHash` - transaction's hash.

### <mark style="color:purple;">approveLinkTopHatToTree</mark>

Approve a tophat's linkage request.

```typescript
const approveLinkTopHatToTreeResult = await hatsClient.approveLinkTopHatToTree({
    account,
    topHatDomain,
    newAdminHat,
    newEligibility,
    newToggle,
    newDetails,
    newImageURI,
});
```

_**Arguments**_:

```typescript
{
    account: Account | Address;
    topHatDomain: number;
    newAdminHat: bigint;
    newEligibility?: Address;
    newToggle?: Address;
    newDetails?: string;
    newImageURI?: string;
}
```

* `account` - Viem account (Address for JSON-RPC accounts or Account for other types).
* `topHatDomain` - the tree domain of the requesting tree. The tree domain is the first four bytes of the tophat ID.
* `newAdminHat` - ID of the new admin hat.
* `newEligibility` - optional new eligibility for the linked tophat.
* `newToggle` - optional new toggle for the linked tophat.
* `newDetails` - optional new details for the linked tophat.
* `newImageURI` - optional new image URI for the linked tophat.

_**Response**_:

```typescript
{
  status: "success" | "reverted";
  transactionHash: `0x${string}`;
}
```

* `status` - "success" if transaction was successful, "reverted" if transaction reverted.
* `transactionHash` - transaction's hash.

### <mark style="color:purple;">unlinkTopHatFromTree</mark>

Unlink a tree.

```typescript
const unlinkTopHatFromTreeResult = await hatsClient.unlinkTopHatFromTree({
    account,
    topHatDomain,
    wearer,
});
```

_**Arguments**_:

```typescript
{
    account: Account | Address;
    topHatDomain: number;
    wearer: Address;
}
```

* `account` - Viem account (Address for JSON-RPC accounts or Account for other types).
* `topHatDomain` - the tree domain. The tree domain is the first four bytes of the tophat ID.
* `wearer` - The current wearer of the tophat that is about to be unlinked.

_**Response**_:

```typescript
{
  status: "success" | "reverted";
  transactionHash: `0x${string}`;
}
```

* `status` - "success" if transaction was successful, "reverted" if transaction reverted.
* `transactionHash` - transaction's hash.

### <mark style="color:purple;">relinkTopHatWithinTree</mark>

Relink a tree within the same global tree that it is already part of.

```typescript
const relinkTopHatWithinTreeResult = await hatsClient.relinkTopHatWithinTree({
    account,
    topHatDomain,
    newAdminHat,
    newEligibility,
    newToggle,
    newDetails,
    newImageURI,
});
```

_**Arguments**_:

```typescript
{
    account: Account | Address;
    topHatDomain: number;
    newAdminHat: bigint;
    newEligibility?: Address;
    newToggle?: Address;
    newDetails?: string;
    newImageURI?: string;
}
```

* `account` - Viem account (Address for JSON-RPC accounts or Account for other types).
* `topHatDomain` - the tree domain of the relinked tree. The tree domain is the first four bytes of the tophat ID.
* `newAdminHat` - ID of the new admin hat.
* `newEligibility` - optional new eligibility for the linked tophat.
* `newToggle` - optional new toggle for the linked tophat.
* `newDetails` - optional new details for the linked tophat.
* `newImageURI` - optional new image URI for the linked tophat.

_**Response**_:

```typescript
{
  status: "success" | "reverted";
  transactionHash: `0x${string}`;
}
```

* `status` - "success" if transaction was successful, "reverted" if transaction reverted.
* `transactionHash` - transaction's hash.
