# HatsErrors.sol

## HatsErrors

[Git Source](https://github.com/Hats-Protocol/hats-protocol/blob/b43ad0d1dbe4a4190febc036ee8a2849e3f221b4/src/Interfaces/HatsErrors.sol)

### Errors

#### NotAdmin

Emitted when `user` is attempting to perform an action on `hatId` but is not wearing one of `hatId`'s admin hats

_Can be equivalent to `NotHatWearer(buildHatId(hatId))`, such as when emitted by `approveLinkTopHatToTree` or `relinkTopHatToTree`_

```solidity
error NotAdmin(address user, uint256 hatId);
```

#### NotHatWearer

Emitted when attempting to perform an action as or for an account that is not a wearer of a given hat

```solidity
error NotHatWearer();
```

#### NotAdminOrWearer

Emitted when attempting to perform an action that requires being either an admin or wearer of a given hat

```solidity
error NotAdminOrWearer();
```

#### AllHatsWorn

Emitted when attempting to mint `hatId` but `hatId`'s maxSupply has been reached

```solidity
error AllHatsWorn(uint256 hatId);
```

#### MaxLevelsReached

Emitted when attempting to create a hat with a level 14 hat as its admin

```solidity
error MaxLevelsReached();
```

#### InvalidHatId

Emitted when an attempted hat id has empty intermediate level(s)

```solidity
error InvalidHatId();
```

#### AlreadyWearingHat

Emitted when attempting to mint `hatId` to a `wearer` who is already wearing the hat

```solidity
error AlreadyWearingHat(address wearer, uint256 hatId);
```

#### HatDoesNotExist

Emitted when attempting to mint a non-existant hat

```solidity
error HatDoesNotExist(uint256 hatId);
```

#### HatNotActive

Emmitted when attempting to mint or transfer a hat that is not active

```solidity
error HatNotActive();
```

#### NotEligible

Emitted when attempting to mint or transfer a hat to an ineligible wearer

```solidity
error NotEligible();
```

#### NotHatsToggle

Emitted when attempting to check or set a hat's status from an account that is not that hat's toggle module

```solidity
error NotHatsToggle();
```

#### NotHatsEligibility

Emitted when attempting to check or set a hat wearer's status from an account that is not that hat's eligibility module

```solidity
error NotHatsEligibility();
```

#### BatchArrayLengthMismatch

Emitted when array arguments to a batch function have mismatching lengths

```solidity
error BatchArrayLengthMismatch();
```

#### Immutable

Emitted when attempting to mutate or transfer an immutable hat

```solidity
error Immutable();
```

#### NewMaxSupplyTooLow

Emitted when attempting to change a hat's maxSupply to a value lower than its current supply

```solidity
error NewMaxSupplyTooLow();
```

#### CircularLinkage

Emitted when attempting to link a tophat to a new admin for which the tophat serves as an admin

```solidity
error CircularLinkage();
```

#### CrossTreeLinkage

Emitted when attempting to link or relink a tophat to a separate tree

```solidity
error CrossTreeLinkage();
```

#### LinkageNotRequested

Emitted when attempting to link a tophat without a request

```solidity
error LinkageNotRequested();
```

#### InvalidUnlink

Emitted when attempting to unlink a tophat that does not have a wearer

_This ensures that unlinking never results in a bricked tophat_

```solidity
error InvalidUnlink();
```

#### ZeroAddress

Emmited when attempting to change a hat's eligibility or toggle module to the zero address

```solidity
error ZeroAddress();
```

#### StringTooLong

Emmitted when attempting to change a hat's details or imageURI to a string with over 7000 bytes (\~characters)

_This protects against a DOS attack where an admin iteratively extend's a hat's details or imageURI to be so long that reading it exceeds the block gas limit, breaking `uri()` and `viewHat()`_

```solidity
error StringTooLong();
```
