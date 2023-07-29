# IHatsIdUtilities.sol

## IHatsIdUtilities

[Git Source](https://github.com/Hats-Protocol/hats-protocol/blob/b43ad0d1dbe4a4190febc036ee8a2849e3f221b4/src/Interfaces/IHatsIdUtilities.sol)

### Functions

#### buildHatId

```solidity
function buildHatId(uint256 _admin, uint16 _newHat) external pure returns (uint256 id);
```

#### getHatLevel

```solidity
function getHatLevel(uint256 _hatId) external view returns (uint32 level);
```

#### getLocalHatLevel

```solidity
function getLocalHatLevel(uint256 _hatId) external pure returns (uint32 level);
```

#### isTopHat

```solidity
function isTopHat(uint256 _hatId) external view returns (bool _topHat);
```

#### isLocalTopHat

```solidity
function isLocalTopHat(uint256 _hatId) external pure returns (bool _localTopHat);
```

#### isValidHatId

```solidity
function isValidHatId(uint256 _hatId) external view returns (bool validHatId);
```

#### getAdminAtLevel

```solidity
function getAdminAtLevel(uint256 _hatId, uint32 _level) external view returns (uint256 admin);
```

#### getAdminAtLocalLevel

```solidity
function getAdminAtLocalLevel(uint256 _hatId, uint32 _level) external pure returns (uint256 admin);
```

#### getTopHatDomain

```solidity
function getTopHatDomain(uint256 _hatId) external view returns (uint32 domain);
```

#### getTippyTopHatDomain

```solidity
function getTippyTopHatDomain(uint32 _topHatDomain) external view returns (uint32 domain);
```

#### noCircularLinkage

```solidity
function noCircularLinkage(uint32 _topHatDomain, uint256 _linkedAdmin) external view returns (bool notCircular);
```

#### sameTippyTopHatDomain

```solidity
function sameTippyTopHatDomain(uint32 _topHatDomain, uint256 _newAdminHat) external view returns (bool sameDomain);
```
