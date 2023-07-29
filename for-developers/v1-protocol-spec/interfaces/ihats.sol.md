# IHats.sol

## IHats

[Git Source](https://github.com/Hats-Protocol/hats-protocol/blob/b43ad0d1dbe4a4190febc036ee8a2849e3f221b4/src/Interfaces/IHats.sol)

**Inherits:** IHatsIdUtilities, HatsErrors, HatsEvents

### Functions

#### mintTopHat

```solidity
function mintTopHat(address _target, string memory _details, string memory _imageURI)
    external
    returns (uint256 topHatId);
```

#### createHat

```solidity
function createHat(
    uint256 _admin,
    string calldata _details,
    uint32 _maxSupply,
    address _eligibility,
    address _toggle,
    bool _mutable,
    string calldata _imageURI
) external returns (uint256 newHatId);
```

#### batchCreateHats

```solidity
function batchCreateHats(
    uint256[] calldata _admins,
    string[] calldata _details,
    uint32[] calldata _maxSupplies,
    address[] memory _eligibilityModules,
    address[] memory _toggleModules,
    bool[] calldata _mutables,
    string[] calldata _imageURIs
) external returns (bool success);
```

#### getNextId

```solidity
function getNextId(uint256 _admin) external view returns (uint256 nextId);
```

#### mintHat

```solidity
function mintHat(uint256 _hatId, address _wearer) external returns (bool success);
```

#### batchMintHats

```solidity
function batchMintHats(uint256[] calldata _hatIds, address[] calldata _wearers) external returns (bool success);
```

#### setHatStatus

```solidity
function setHatStatus(uint256 _hatId, bool _newStatus) external returns (bool toggled);
```

#### checkHatStatus

```solidity
function checkHatStatus(uint256 _hatId) external returns (bool toggled);
```

#### setHatWearerStatus

```solidity
function setHatWearerStatus(uint256 _hatId, address _wearer, bool _eligible, bool _standing)
    external
    returns (bool updated);
```

#### checkHatWearerStatus

```solidity
function checkHatWearerStatus(uint256 _hatId, address _wearer) external returns (bool updated);
```

#### renounceHat

```solidity
function renounceHat(uint256 _hatId) external;
```

#### transferHat

```solidity
function transferHat(uint256 _hatId, address _from, address _to) external;
```

#### makeHatImmutable

```solidity
function makeHatImmutable(uint256 _hatId) external;
```

#### changeHatDetails

```solidity
function changeHatDetails(uint256 _hatId, string memory _newDetails) external;
```

#### changeHatEligibility

```solidity
function changeHatEligibility(uint256 _hatId, address _newEligibility) external;
```

#### changeHatToggle

```solidity
function changeHatToggle(uint256 _hatId, address _newToggle) external;
```

#### changeHatImageURI

```solidity
function changeHatImageURI(uint256 _hatId, string memory _newImageURI) external;
```

#### changeHatMaxSupply

```solidity
function changeHatMaxSupply(uint256 _hatId, uint32 _newMaxSupply) external;
```

#### requestLinkTopHatToTree

```solidity
function requestLinkTopHatToTree(uint32 _topHatId, uint256 _newAdminHat) external;
```

#### approveLinkTopHatToTree

```solidity
function approveLinkTopHatToTree(
    uint32 _topHatId,
    uint256 _newAdminHat,
    address _eligibility,
    address _toggle,
    string calldata _details,
    string calldata _imageURI
) external;
```

#### unlinkTopHatFromTree

```solidity
function unlinkTopHatFromTree(uint32 _topHatId, address _wearer) external;
```

#### relinkTopHatWithinTree

```solidity
function relinkTopHatWithinTree(
    uint32 _topHatDomain,
    uint256 _newAdminHat,
    address _eligibility,
    address _toggle,
    string calldata _details,
    string calldata _imageURI
) external;
```

#### viewHat

```solidity
function viewHat(uint256 _hatId)
    external
    view
    returns (
        string memory details,
        uint32 maxSupply,
        uint32 supply,
        address eligibility,
        address toggle,
        string memory imageURI,
        uint16 lastHatId,
        bool mutable_,
        bool active
    );
```

#### isWearerOfHat

```solidity
function isWearerOfHat(address _user, uint256 _hatId) external view returns (bool isWearer);
```

#### isAdminOfHat

```solidity
function isAdminOfHat(address _user, uint256 _hatId) external view returns (bool isAdmin);
```

#### isInGoodStanding

```solidity
function isInGoodStanding(address _wearer, uint256 _hatId) external view returns (bool standing);
```

#### isEligible

```solidity
function isEligible(address _wearer, uint256 _hatId) external view returns (bool eligible);
```

#### getHatEligibilityModule

```solidity
function getHatEligibilityModule(uint256 _hatId) external view returns (address eligibility);
```

#### getHatToggleModule

```solidity
function getHatToggleModule(uint256 _hatId) external view returns (address toggle);
```

#### getHatMaxSupply

```solidity
function getHatMaxSupply(uint256 _hatId) external view returns (uint32 maxSupply);
```

#### hatSupply

```solidity
function hatSupply(uint256 _hatId) external view returns (uint32 supply);
```

#### getImageURIForHat

```solidity
function getImageURIForHat(uint256 _hatId) external view returns (string memory _uri);
```

#### balanceOf

```solidity
function balanceOf(address wearer, uint256 hatId) external view returns (uint256 balance);
```

#### balanceOfBatch

```solidity
function balanceOfBatch(address[] calldata _wearers, uint256[] calldata _hatIds)
    external
    view
    returns (uint256[] memory);
```

#### uri

```solidity
function uri(uint256 id) external view returns (string memory _uri);
```
