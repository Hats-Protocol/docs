# HatsEvents.sol

## HatsEvents

[Git Source](https://github.com/Hats-Protocol/hats-protocol/blob/b43ad0d1dbe4a4190febc036ee8a2849e3f221b4/src/Interfaces/HatsEvents.sol)

### Events

#### HatCreated

Emitted when a new hat is created

```solidity
event HatCreated(
    uint256 id, string details, uint32 maxSupply, address eligibility, address toggle, bool mutable_, string imageURI
);
```

#### WearerStandingChanged

Emitted when a hat wearer's standing is updated

_Eligibility is excluded since the source of truth for eligibility is the eligibility module and may change without a transaction_

```solidity
event WearerStandingChanged(uint256 hatId, address wearer, bool wearerStanding);
```

#### HatStatusChanged

Emitted when a hat's status is updated

```solidity
event HatStatusChanged(uint256 hatId, bool newStatus);
```

#### HatDetailsChanged

Emitted when a hat's details are updated

```solidity
event HatDetailsChanged(uint256 hatId, string newDetails);
```

#### HatEligibilityChanged

Emitted when a hat's eligibility module is updated

```solidity
event HatEligibilityChanged(uint256 hatId, address newEligibility);
```

#### HatToggleChanged

Emitted when a hat's toggle module is updated

```solidity
event HatToggleChanged(uint256 hatId, address newToggle);
```

#### HatMutabilityChanged

Emitted when a hat's mutability is updated

```solidity
event HatMutabilityChanged(uint256 hatId);
```

#### HatMaxSupplyChanged

Emitted when a hat's maximum supply is updated

```solidity
event HatMaxSupplyChanged(uint256 hatId, uint32 newMaxSupply);
```

#### HatImageURIChanged

Emitted when a hat's image URI is updated

```solidity
event HatImageURIChanged(uint256 hatId, string newImageURI);
```

#### TopHatLinkRequested

Emitted when a tophat linkage is requested by its admin

```solidity
event TopHatLinkRequested(uint32 domain, uint256 newAdmin);
```

#### TopHatLinked

Emitted when a tophat is linked to a another tree

```solidity
event TopHatLinked(uint32 domain, uint256 newAdmin);
```
