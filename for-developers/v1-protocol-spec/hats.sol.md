# Hats.sol

## Hats

[Git Source](https://github.com/Hats-Protocol/hats-protocol/blob/b43ad0d1dbe4a4190febc036ee8a2849e3f221b4/src/Hats.sol)

**Inherits:** IHats, ERC1155, Multicallable, HatsIdUtilities

**Author:** Haberdasher Labs

Hats are DAO-native, revocable, and programmable roles that are represented as non-transferable ERC-1155-similar tokens for composability

_This is a multi-tenant contract that can manage all hats for a given chain. While it fully implements the ERC1155 interface, it does not fully comply with the ERC1155 standard._

### State Variables

#### name

The name of the contract, typically including the version

```solidity
string public name;
```

#### lastTopHatId

The first 4 bytes of the id of the last tophat created.

```solidity
uint32 public lastTopHatId;
```

#### baseImageURI

The fallback image URI for hat tokens with no `imageURI` specified in their branch

```solidity
string public baseImageURI;
```

#### \_hats

_Internal mapping of hats to hat ids. See HatsIdUtilities.sol for more info on how hat ids work_

```solidity
mapping(uint256 => Hat) internal _hats;
```

#### badStandings

Mapping of wearers in bad standing for certain hats

_Used by external contracts to trigger penalties for wearers in bad standing hatId => wearer => !standing_

```solidity
mapping(uint256 => mapping(address => bool)) public badStandings;
```

### Functions

#### constructor

All arguments are immutable; they can only be set once during construction

```solidity
constructor(string memory _name, string memory _baseImageURI);
```

**Parameters**

| Name            | Type     | Description                                                |
| --------------- | -------- | ---------------------------------------------------------- |
| `_name`         | `string` | The name of this contract, typically including the version |
| `_baseImageURI` | `string` | The fallback image URI                                     |

#### mintTopHat

Creates and mints a Hat that is its own admin, i.e. a "topHat"

_A topHat has no eligibility and no toggle_

```solidity
function mintTopHat(address _target, string calldata _details, string calldata _imageURI)
    public
    returns (uint256 topHatId);
```

**Parameters**

| Name        | Type      | Description                                                                                                                                              |
| ----------- | --------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `_target`   | `address` | The address to which the newly created topHat is minted                                                                                                  |
| `_details`  | `string`  | A description of the Hat \[optional]. Should not be larger than 7000 bytes (enforced in changeHatDetails)                                                |
| `_imageURI` | `string`  | The image uri for this top hat and the fallback for its downstream hats \[optional]. Should not be large than 7000 bytes (enforced in changeHatImageURI) |

**Returns**

| Name       | Type      | Description                        |
| ---------- | --------- | ---------------------------------- |
| `topHatId` | `uint256` | The id of the newly created topHat |

#### createHat

Creates a new hat. The msg.sender must wear the `_admin` hat.

_Initializes a new Hat struct, but does not mint any tokens._

```solidity
function createHat(
    uint256 _admin,
    string calldata _details,
    uint32 _maxSupply,
    address _eligibility,
    address _toggle,
    bool _mutable,
    string calldata _imageURI
) public returns (uint256 newHatId);
```

**Parameters**

| Name           | Type      | Description                                                                                                                                           |
| -------------- | --------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| `_admin`       | `uint256` | The id of the Hat that will control who wears the newly created hat                                                                                   |
| `_details`     | `string`  | A description of the Hat. Should not be larger than 7000 bytes (enforced in changeHatDetails)                                                         |
| `_maxSupply`   | `uint32`  | The total instances of the Hat that can be worn at once                                                                                               |
| `_eligibility` | `address` | The address that can report on the Hat wearer's status                                                                                                |
| `_toggle`      | `address` | The address that can deactivate the Hat                                                                                                               |
| `_mutable`     | `bool`    | Whether the hat's properties are changeable after creation                                                                                            |
| `_imageURI`    | `string`  | The image uri for this hat and the fallback for its downstream hats \[optional]. Should not be larger than 7000 bytes (enforced in changeHatImageURI) |

**Returns**

| Name       | Type      | Description                     |
| ---------- | --------- | ------------------------------- |
| `newHatId` | `uint256` | The id of the newly created Hat |

#### batchCreateHats

Creates new hats in batch. The msg.sender must be an admin of each hat.

_This is a convenience function that loops through the arrays and calls `createHat`._

```solidity
function batchCreateHats(
    uint256[] calldata _admins,
    string[] calldata _details,
    uint32[] calldata _maxSupplies,
    address[] memory _eligibilityModules,
    address[] memory _toggleModules,
    bool[] calldata _mutables,
    string[] calldata _imageURIs
) public returns (bool success);
```

**Parameters**

| Name                  | Type        | Description                                                  |
| --------------------- | ----------- | ------------------------------------------------------------ |
| `_admins`             | `uint256[]` | Array of ids of admins for each hat to create                |
| `_details`            | `string[]`  | Array of details for each hat to create                      |
| `_maxSupplies`        | `uint32[]`  | Array of supply caps for each hat to create                  |
| `_eligibilityModules` | `address[]` | Array of eligibility module addresses for each hat to create |
| `_toggleModules`      | `address[]` | Array of toggle module addresses for each hat to create      |
| `_mutables`           | `bool[]`    | Array of mutable flags for each hat to create                |
| `_imageURIs`          | `string[]`  | Array of imageURIs for each hat to create                    |

**Returns**

| Name      | Type   | Description                           |
| --------- | ------ | ------------------------------------- |
| `success` | `bool` | True if all createHat calls succeeded |

#### getNextId

Gets the id of the next child hat of the hat `_admin`

_Does not incrememnt lastHatId_

```solidity
function getNextId(uint256 _admin) public view returns (uint256 nextId);
```

**Parameters**

| Name     | Type      | Description                                                    |
| -------- | --------- | -------------------------------------------------------------- |
| `_admin` | `uint256` | The id of the hat to serve as the admin for the next child hat |

**Returns**

| Name     | Type      | Description    |
| -------- | --------- | -------------- |
| `nextId` | `uint256` | The new hat id |

#### mintHat

Mints an ERC1155-similar token of the Hat to an eligible recipient, who then "wears" the hat

_The msg.sender must wear an admin Hat of `_hatId`, and the recipient must be eligible to wear `_hatId`_

```solidity
function mintHat(uint256 _hatId, address _wearer) public returns (bool success);
```

**Parameters**

| Name      | Type      | Description                            |
| --------- | --------- | -------------------------------------- |
| `_hatId`  | `uint256` | The id of the Hat to mint              |
| `_wearer` | `address` | The address to which the Hat is minted |

**Returns**

| Name      | Type   | Description                |
| --------- | ------ | -------------------------- |
| `success` | `bool` | Whether the mint succeeded |

#### batchMintHats

Mints new hats in batch. The msg.sender must be an admin of each hat.

_This is a convenience function that loops through the arrays and calls `mintHat`._

```solidity
function batchMintHats(uint256[] calldata _hatIds, address[] calldata _wearers) public returns (bool success);
```

**Parameters**

| Name       | Type        | Description                                         |
| ---------- | ----------- | --------------------------------------------------- |
| `_hatIds`  | `uint256[]` | Array of ids of hats to mint                        |
| `_wearers` | `address[]` | Array of addresses to which the hats will be minted |

**Returns**

| Name      | Type   | Description                         |
| --------- | ------ | ----------------------------------- |
| `success` | `bool` | True if all mintHat calls succeeded |

#### setHatStatus

Toggles a Hat's status from active to deactive, or vice versa

_The msg.sender must be set as the hat's toggle_

```solidity
function setHatStatus(uint256 _hatId, bool _newStatus) external returns (bool toggled);
```

**Parameters**

| Name         | Type      | Description                                  |
| ------------ | --------- | -------------------------------------------- |
| `_hatId`     | `uint256` | The id of the Hat for which to adjust status |
| `_newStatus` | `bool`    | The new status to set                        |

**Returns**

| Name      | Type   | Description                    |
| --------- | ------ | ------------------------------ |
| `toggled` | `bool` | Whether the status was toggled |

#### checkHatStatus

Checks a hat's toggle module and processes the returned status

_May change the hat's status in storage_

```solidity
function checkHatStatus(uint256 _hatId) public returns (bool toggled);
```

**Parameters**

| Name     | Type      | Description                                    |
| -------- | --------- | ---------------------------------------------- |
| `_hatId` | `uint256` | The id of the Hat whose toggle we are checking |

**Returns**

| Name      | Type   | Description                    |
| --------- | ------ | ------------------------------ |
| `toggled` | `bool` | Whether there was a new status |

#### \_pullHatStatus

```solidity
function _pullHatStatus(Hat storage _hat, uint256 _hatId) internal view returns (bool success, bool newStatus);
```

#### setHatWearerStatus

Report from a hat's eligibility on the status of one of its wearers and, if `false`, revoke their hat

_Burns the wearer's hat, if revoked_

```solidity
function setHatWearerStatus(uint256 _hatId, address _wearer, bool _eligible, bool _standing)
    external
    returns (bool updated);
```

**Parameters**

| Name        | Type      | Description                                                                             |
| ----------- | --------- | --------------------------------------------------------------------------------------- |
| `_hatId`    | `uint256` | The id of the hat                                                                       |
| `_wearer`   | `address` | The address of the hat wearer whose status is being reported                            |
| `_eligible` | `bool`    | Whether the wearer is eligible for the hat (will be revoked if false)                   |
| `_standing` | `bool`    | False if the wearer is no longer in good standing (and potentially should be penalized) |

**Returns**

| Name      | Type   | Description                  |
| --------- | ------ | ---------------------------- |
| `updated` | `bool` | Whether the report succeeded |

#### checkHatWearerStatus

Check a hat's eligibility for a report on the status of one of the hat's wearers and, if `false`, revoke their hat

_Burns the wearer's hat, if revoked_

```solidity
function checkHatWearerStatus(uint256 _hatId, address _wearer) public returns (bool updated);
```

**Parameters**

| Name      | Type      | Description                                                          |
| --------- | --------- | -------------------------------------------------------------------- |
| `_hatId`  | `uint256` | The id of the hat                                                    |
| `_wearer` | `address` | The address of the Hat wearer whose status report is being requested |

**Returns**

| Name      | Type   | Description                             |
| --------- | ------ | --------------------------------------- |
| `updated` | `bool` | Whether the wearer's status was altered |

#### renounceHat

Stop wearing a hat, aka "renounce" it

_Burns the msg.sender's hat_

```solidity
function renounceHat(uint256 _hatId) external;
```

**Parameters**

| Name     | Type      | Description                       |
| -------- | --------- | --------------------------------- |
| `_hatId` | `uint256` | The id of the Hat being renounced |

#### \_createHat

Internal call for creating a new hat

_Initializes a new Hat in storage, but does not mint any tokens_

```solidity
function _createHat(
    uint256 _id,
    string calldata _details,
    uint32 _maxSupply,
    address _eligibility,
    address _toggle,
    bool _mutable,
    string calldata _imageURI
) internal;
```

**Parameters**

| Name           | Type      | Description                                                                         |
| -------------- | --------- | ----------------------------------------------------------------------------------- |
| `_id`          | `uint256` | ID of the hat to be stored                                                          |
| `_details`     | `string`  | A description of the hat                                                            |
| `_maxSupply`   | `uint32`  | The total instances of the Hat that can be worn at once                             |
| `_eligibility` | `address` | The address that can report on the Hat wearer's status                              |
| `_toggle`      | `address` | The address that can deactivate the hat \[optional]                                 |
| `_mutable`     | `bool`    | Whether the hat's properties are changeable after creation                          |
| `_imageURI`    | `string`  | The image uri for this top hat and the fallback for its downstream hats \[optional] |

#### \_processHatStatus

Internal function to process hat status

_Updates a hat's status if different from current_

```solidity
function _processHatStatus(uint256 _hatId, bool _newStatus) internal returns (bool updated);
```

**Parameters**

| Name         | Type      | Description                         |
| ------------ | --------- | ----------------------------------- |
| `_hatId`     | `uint256` | The id of the Hat in quest          |
| `_newStatus` | `bool`    | The status to potentially change to |

**Returns**

| Name      | Type   | Description                      |
| --------- | ------ | -------------------------------- |
| `updated` | `bool` | - Whether the status was updated |

#### \_processHatWearerStatus

Internal call to process wearer status from the eligibility module

_Burns the wearer's Hat token if \_eligible is false, and updates badStandings state if necessary_

```solidity
function _processHatWearerStatus(uint256 _hatId, address _wearer, bool _eligible, bool _standing)
    internal
    returns (bool updated);
```

**Parameters**

| Name        | Type      | Description                                                                              |
| ----------- | --------- | ---------------------------------------------------------------------------------------- |
| `_hatId`    | `uint256` | The id of the Hat to revoke                                                              |
| `_wearer`   | `address` | The address of the wearer in question                                                    |
| `_eligible` | `bool`    | Whether \_wearer is eligible for the Hat (if false, this function will revoke their Hat) |
| `_standing` | `bool`    | Whether \_wearer is in good standing (to be recorded in storage)                         |

**Returns**

| Name      | Type   | Description                             |
| --------- | ------ | --------------------------------------- |
| `updated` | `bool` | Whether the wearer standing was updated |

#### \_setHatStatus

Internal function to set a hat's status in storage

_Flips the 0th bit of \_hat.config via bitwise operation_

```solidity
function _setHatStatus(Hat storage _hat, bool _status) internal;
```

**Parameters**

| Name      | Type   | Description                   |
| --------- | ------ | ----------------------------- |
| `_hat`    | `Hat`  | The hat object                |
| `_status` | `bool` | The status to set for the hat |

#### \_staticBalanceOf

Internal function to retrieve an account's internal "static" balance directly from internal storage,

_This function bypasses the dynamic `_isActive` and `_isEligible` checks_

```solidity
function _staticBalanceOf(address _account, uint256 _hatId) internal view returns (uint256 staticBalance);
```

**Parameters**

| Name       | Type      | Description          |
| ---------- | --------- | -------------------- |
| `_account` | `address` | The account to check |
| `_hatId`   | `uint256` | The hat to check     |

**Returns**

| Name            | Type      | Description                                            |
| --------------- | --------- | ------------------------------------------------------ |
| `staticBalance` | `uint256` | The account's static of the hat, from internal storage |

#### \_checkAdmin

Checks whether msg.sender is an admin of a hat, and reverts if not

```solidity
function _checkAdmin(uint256 _hatId) internal view;
```

#### \_checkAdminOrWearer

checks whether the msg.sender is either an admin or wearer or a hat, and reverts the appropriate error if not

```solidity
function _checkAdminOrWearer(uint256 _hatId) internal view;
```

#### transferHat

Transfers a hat from one wearer to another eligible wearer

_The hat must be mutable, and the transfer must be initiated by an admin_

```solidity
function transferHat(uint256 _hatId, address _from, address _to) public;
```

**Parameters**

| Name     | Type      | Description         |
| -------- | --------- | ------------------- |
| `_hatId` | `uint256` | The hat in question |
| `_from`  | `address` | The current wearer  |
| `_to`    | `address` | The new wearer      |

#### makeHatImmutable

Set a mutable hat to immutable

_Sets the second bit of hat.config to 0_

```solidity
function makeHatImmutable(uint256 _hatId) external;
```

**Parameters**

| Name     | Type      | Description                         |
| -------- | --------- | ----------------------------------- |
| `_hatId` | `uint256` | The id of the Hat to make immutable |

#### changeHatDetails

Change a hat's details

_Hat must be mutable, except for tophats._

```solidity
function changeHatDetails(uint256 _hatId, string calldata _newDetails) external;
```

**Parameters**

| Name          | Type      | Description                                          |
| ------------- | --------- | ---------------------------------------------------- |
| `_hatId`      | `uint256` | The id of the Hat to change                          |
| `_newDetails` | `string`  | The new details. Must not be larger than 7000 bytes. |

#### changeHatEligibility

Change a hat's details

_Hat must be mutable_

```solidity
function changeHatEligibility(uint256 _hatId, address _newEligibility) external;
```

**Parameters**

| Name              | Type      | Description                 |
| ----------------- | --------- | --------------------------- |
| `_hatId`          | `uint256` | The id of the Hat to change |
| `_newEligibility` | `address` | The new eligibility module  |

#### changeHatToggle

Change a hat's details

_Hat must be mutable_

```solidity
function changeHatToggle(uint256 _hatId, address _newToggle) external;
```

**Parameters**

| Name         | Type      | Description                 |
| ------------ | --------- | --------------------------- |
| `_hatId`     | `uint256` | The id of the Hat to change |
| `_newToggle` | `address` | The new toggle module       |

#### changeHatImageURI

Change a hat's details

_Hat must be mutable, except for tophats_

```solidity
function changeHatImageURI(uint256 _hatId, string calldata _newImageURI) external;
```

**Parameters**

| Name           | Type      | Description                                           |
| -------------- | --------- | ----------------------------------------------------- |
| `_hatId`       | `uint256` | The id of the Hat to change                           |
| `_newImageURI` | `string`  | The new imageURI. Must not be larger than 7000 bytes. |

#### changeHatMaxSupply

Change a hat's details

_Hat must be mutable; new max supply cannot be less than current supply_

```solidity
function changeHatMaxSupply(uint256 _hatId, uint32 _newMaxSupply) external;
```

**Parameters**

| Name            | Type      | Description                 |
| --------------- | --------- | --------------------------- |
| `_hatId`        | `uint256` | The id of the Hat to change |
| `_newMaxSupply` | `uint32`  | The new max supply          |

#### requestLinkTopHatToTree

Submits a request to link a Hat Tree under a parent tree. Requests can be submitted by either... a) the wearer of a topHat, previous to any linkage, or b) the admin(s) of an already-linked topHat (aka tree root), where such a request is to move the tree root to another admin within the same parent tree

_A topHat can have at most 1 request at a time. Submitting a new request will replace the existing request._

```solidity
function requestLinkTopHatToTree(uint32 _topHatDomain, uint256 _requestedAdminHat) external;
```

**Parameters**

| Name                 | Type      | Description                                  |
| -------------------- | --------- | -------------------------------------------- |
| `_topHatDomain`      | `uint32`  | The domain of the topHat to link             |
| `_requestedAdminHat` | `uint256` | The hat that will administer the linked tree |

#### approveLinkTopHatToTree

Approve a request to link a Tree under a parent tree, with options to add eligibility or toggle modules and change its metadata

_Requests can only be approved by wearer or an admin of the `_newAdminHat`, and there can only be one link per tree root at a given time._

```solidity
function approveLinkTopHatToTree(
    uint32 _topHatDomain,
    uint256 _newAdminHat,
    address _eligibility,
    address _toggle,
    string calldata _details,
    string calldata _imageURI
) external;
```

**Parameters**

| Name            | Type      | Description                                           |
| --------------- | --------- | ----------------------------------------------------- |
| `_topHatDomain` | `uint32`  | The 32 bit domain of the topHat to link               |
| `_newAdminHat`  | `uint256` | The hat that will administer the linked tree          |
| `_eligibility`  | `address` | Optional new eligibility module for the linked topHat |
| `_toggle`       | `address` | Optional new toggle module for the linked topHat      |
| `_details`      | `string`  | Optional new details for the linked topHat            |
| `_imageURI`     | `string`  | Optional new imageURI for the linked topHat           |

#### unlinkTopHatFromTree

Unlink a Tree from the parent tree

\*This can only be called by an admin of the tree root. Fails if the topHat to unlink has no non-zero wearer, which can occur if...

* It's wearer is in badStanding
* It has been revoked from its wearer (and possibly burned)˘
* It is not active (ie toggled off)\*

```solidity
function unlinkTopHatFromTree(uint32 _topHatDomain, address _wearer) external;
```

**Parameters**

| Name            | Type      | Description                                |
| --------------- | --------- | ------------------------------------------ |
| `_topHatDomain` | `uint32`  | The 32 bit domain of the topHat to unlink  |
| `_wearer`       | `address` | The current wearer of the topHat to unlink |

#### relinkTopHatWithinTree

Move a tree root to a different position within the same parent tree, without a request. Valid destinations include within the same local tree as the origin, or to the local tree of the tippyTopHat. TippyTopHat wearers can bypass this restriction to relink to anywhere in its full tree.

_Caller must be both an admin tree root and admin or wearer of `_newAdminHat`._

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

**Parameters**

| Name            | Type      | Description                                           |
| --------------- | --------- | ----------------------------------------------------- |
| `_topHatDomain` | `uint32`  | The 32 bit domain of the topHat to relink             |
| `_newAdminHat`  | `uint256` | The new admin for the linked tree                     |
| `_eligibility`  | `address` | Optional new eligibility module for the linked topHat |
| `_toggle`       | `address` | Optional new toggle module for the linked topHat      |
| `_details`      | `string`  | Optional new details for the linked topHat            |
| `_imageURI`     | `string`  | Optional new imageURI for the linked topHat           |

#### \_linkTopHatToTree

Internal function to link a Tree under a parent Tree, with protection against circular linkages and relinking to a separate Tree, with options to add eligibility or toggle modules and change its metadata

_Linking `_topHatDomain` replaces any existing links_

```solidity
function _linkTopHatToTree(
    uint32 _topHatDomain,
    uint256 _newAdminHat,
    address _eligibility,
    address _toggle,
    string calldata _details,
    string calldata _imageURI
) internal;
```

**Parameters**

| Name            | Type      | Description                                           |
| --------------- | --------- | ----------------------------------------------------- |
| `_topHatDomain` | `uint32`  | The 32 bit domain of the topHat to link               |
| `_newAdminHat`  | `uint256` | The new admin for the linked tree                     |
| `_eligibility`  | `address` | Optional new eligibility module for the linked topHat |
| `_toggle`       | `address` | Optional new toggle module for the linked topHat      |
| `_details`      | `string`  | Optional new details for the linked topHat            |
| `_imageURI`     | `string`  | Optional new imageURI for the linked topHat           |

#### viewHat

View the properties of a given Hat

```solidity
function viewHat(uint256 _hatId)
    public
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

**Parameters**

| Name     | Type      | Description       |
| -------- | --------- | ----------------- |
| `_hatId` | `uint256` | The id of the Hat |

**Returns**

| Name          | Type      | Description                                                                                         |
| ------------- | --------- | --------------------------------------------------------------------------------------------------- |
| `details`     | `string`  | The details of the Hat                                                                              |
| `maxSupply`   | `uint32`  | The max supply of tokens for this Hat                                                               |
| `supply`      | `uint32`  | The number of current wearers of this Hat                                                           |
| `eligibility` | `address` | The eligibility address for this Hat                                                                |
| `toggle`      | `address` | The toggle address for this Hat                                                                     |
| `imageURI`    | `string`  | The image URI used for this Hat                                                                     |
| `lastHatId`   | `uint16`  | The most recently created Hat with this Hat as admin; also the count of Hats with this Hat as admin |
| `mutable_`    | `bool`    | Whether this hat's properties can be changed                                                        |
| `active`      | `bool`    | Whether the Hat is current active, as read from `_isActive`                                         |

#### isWearerOfHat

Checks whether a given address wears a given Hat

_Convenience function that wraps `balanceOf`_

```solidity
function isWearerOfHat(address _user, uint256 _hatId) public view returns (bool isWearer);
```

**Parameters**

| Name     | Type      | Description                                   |
| -------- | --------- | --------------------------------------------- |
| `_user`  | `address` | The address in question                       |
| `_hatId` | `uint256` | The id of the Hat that the `_user` might wear |

**Returns**

| Name       | Type   | Description                        |
| ---------- | ------ | ---------------------------------- |
| `isWearer` | `bool` | Whether the `_user` wears the Hat. |

#### isAdminOfHat

Checks whether a given address serves as the admin of a given Hat

_Recursively checks if `_user` wears the admin Hat of the Hat in question. This is recursive since there may be a string of Hats as admins of Hats._

```solidity
function isAdminOfHat(address _user, uint256 _hatId) public view returns (bool isAdmin);
```

**Parameters**

| Name     | Type      | Description                                                |
| -------- | --------- | ---------------------------------------------------------- |
| `_user`  | `address` | The address in question                                    |
| `_hatId` | `uint256` | The id of the Hat for which the `_user` might be the admin |

**Returns**

| Name      | Type   | Description                                      |
| --------- | ------ | ------------------------------------------------ |
| `isAdmin` | `bool` | Whether the `_user` has admin rights for the Hat |

#### \_isActive

Checks the active status of a hat

_For internal use instead of `isActive` when passing Hat as param is preferable_

```solidity
function _isActive(Hat storage _hat, uint256 _hatId) internal view returns (bool active);
```

**Parameters**

| Name     | Type      | Description       |
| -------- | --------- | ----------------- |
| `_hat`   | `Hat`     | The Hat struct    |
| `_hatId` | `uint256` | The id of the hat |

**Returns**

| Name     | Type   | Description                  |
| -------- | ------ | ---------------------------- |
| `active` | `bool` | The active status of the hat |

#### isActive

Checks the active status of a hat

```solidity
function isActive(uint256 _hatId) external view returns (bool active);
```

**Parameters**

| Name     | Type      | Description       |
| -------- | --------- | ----------------- |
| `_hatId` | `uint256` | The id of the hat |

**Returns**

| Name     | Type   | Description               |
| -------- | ------ | ------------------------- |
| `active` | `bool` | Whether the hat is active |

#### \_getHatStatus

Internal function to retrieve a hat's status from storage

_reads the 0th bit of the hat's config_

```solidity
function _getHatStatus(Hat storage _hat) internal view returns (bool status);
```

**Parameters**

| Name   | Type  | Description    |
| ------ | ----- | -------------- |
| `_hat` | `Hat` | The hat object |

**Returns**

| Name     | Type   | Description               |
| -------- | ------ | ------------------------- |
| `status` | `bool` | Whether the hat is active |

#### \_isMutable

Internal function to retrieve a hat's mutability setting

_reads the 1st bit of the hat's config_

```solidity
function _isMutable(Hat storage _hat) internal view returns (bool _mutable);
```

**Parameters**

| Name   | Type  | Description    |
| ------ | ----- | -------------- |
| `_hat` | `Hat` | The hat object |

**Returns**

| Name       | Type   | Description                |
| ---------- | ------ | -------------------------- |
| `_mutable` | `bool` | Whether the hat is mutable |

#### isInGoodStanding

Checks whether a wearer of a Hat is in good standing

```solidity
function isInGoodStanding(address _wearer, uint256 _hatId) public view returns (bool standing);
```

**Parameters**

| Name      | Type      | Description                   |
| --------- | --------- | ----------------------------- |
| `_wearer` | `address` | The address of the Hat wearer |
| `_hatId`  | `uint256` | The id of the Hat             |

**Returns**

| Name       | Type   | Description                            |
| ---------- | ------ | -------------------------------------- |
| `standing` | `bool` | Whether the wearer is in good standing |

#### \_isEligible

Internal call to check whether an address is eligible for a given Hat

_Tries an external call to the Hat's eligibility module, defaulting to existing badStandings state if the call fails (ie if the eligibility module address does not conform to the IHatsEligibility interface)_

```solidity
function _isEligible(address _wearer, Hat storage _hat, uint256 _hatId) internal view returns (bool eligible);
```

**Parameters**

| Name      | Type      | Description                   |
| --------- | --------- | ----------------------------- |
| `_wearer` | `address` | The address of the Hat wearer |
| `_hat`    | `Hat`     | The Hat object                |
| `_hatId`  | `uint256` | The id of the Hat             |

**Returns**

| Name       | Type   | Description                                |
| ---------- | ------ | ------------------------------------------ |
| `eligible` | `bool` | Whether the wearer is eligible for the Hat |

#### isEligible

Checks whether an address is eligible for a given Hat

_Public function for use when passing a Hat object is not possible or preferable_

```solidity
function isEligible(address _wearer, uint256 _hatId) public view returns (bool eligible);
```

**Parameters**

| Name      | Type      | Description          |
| --------- | --------- | -------------------- |
| `_wearer` | `address` | The address to check |
| `_hatId`  | `uint256` | The id of the Hat    |

**Returns**

| Name       | Type   | Description                                |
| ---------- | ------ | ------------------------------------------ |
| `eligible` | `bool` | Whether the wearer is eligible for the Hat |

#### hatSupply

Gets the current supply of a Hat

_Only tracks explicit burns and mints, not dynamic revocations_

```solidity
function hatSupply(uint256 _hatId) external view returns (uint32 supply);
```

**Parameters**

| Name     | Type      | Description       |
| -------- | --------- | ----------------- |
| `_hatId` | `uint256` | The id of the Hat |

**Returns**

| Name     | Type     | Description                   |
| -------- | -------- | ----------------------------- |
| `supply` | `uint32` | The current supply of the Hat |

#### getHatEligibilityModule

Gets the eligibility module for a hat

```solidity
function getHatEligibilityModule(uint256 _hatId) external view returns (address eligibility);
```

**Parameters**

| Name     | Type      | Description                                        |
| -------- | --------- | -------------------------------------------------- |
| `_hatId` | `uint256` | The hat whose eligibility module we're looking for |

**Returns**

| Name          | Type      | Description                         |
| ------------- | --------- | ----------------------------------- |
| `eligibility` | `address` | The eligibility module for this hat |

#### getHatToggleModule

Gets the toggle module for a hat

```solidity
function getHatToggleModule(uint256 _hatId) external view returns (address toggle);
```

**Parameters**

| Name     | Type      | Description                                   |
| -------- | --------- | --------------------------------------------- |
| `_hatId` | `uint256` | The hat whose toggle module we're looking for |

**Returns**

| Name     | Type      | Description                    |
| -------- | --------- | ------------------------------ |
| `toggle` | `address` | The toggle module for this hat |

#### getHatMaxSupply

Gets the max supply for a hat

```solidity
function getHatMaxSupply(uint256 _hatId) external view returns (uint32 maxSupply);
```

**Parameters**

| Name     | Type      | Description                                |
| -------- | --------- | ------------------------------------------ |
| `_hatId` | `uint256` | The hat whose max supply we're looking for |

**Returns**

| Name        | Type     | Description                                                    |
| ----------- | -------- | -------------------------------------------------------------- |
| `maxSupply` | `uint32` | The maximum possible quantity of this hat that could be minted |

#### getImageURIForHat

Gets the imageURI for a given hat

_If this hat does not have an imageURI set, recursively get the imageURI from its admin_

```solidity
function getImageURIForHat(uint256 _hatId) public view returns (string memory _uri);
```

**Parameters**

| Name     | Type      | Description                              |
| -------- | --------- | ---------------------------------------- |
| `_hatId` | `uint256` | The hat whose imageURI we're looking for |

**Returns**

| Name   | Type     | Description                                      |
| ------ | -------- | ------------------------------------------------ |
| `_uri` | `string` | The imageURI of this hat or, if empty, its admin |

#### \_constructURI

Constructs the URI for a Hat, using data from the Hat struct

```solidity
function _constructURI(uint256 _hatId) internal view returns (string memory _uri);
```

**Parameters**

| Name     | Type      | Description       |
| -------- | --------- | ----------------- |
| `_hatId` | `uint256` | The id of the Hat |

**Returns**

| Name   | Type     | Description                       |
| ------ | -------- | --------------------------------- |
| `_uri` | `string` | An ERC1155-compatible JSON string |

#### balanceOf

Gets the Hat token balance of a user for a given Hat

_Balance is dynamic based on the hat's status and wearer's eligibility, so off-chain balance data indexed from events may not be in sync_

```solidity
function balanceOf(address _wearer, uint256 _hatId) public view override(ERC1155, IHats) returns (uint256 balance);
```

**Parameters**

| Name      | Type      | Description                                |
| --------- | --------- | ------------------------------------------ |
| `_wearer` | `address` | The address whose balance is being checked |
| `_hatId`  | `uint256` | The id of the Hat                          |

**Returns**

| Name      | Type      | Description                                                 |
| --------- | --------- | ----------------------------------------------------------- |
| `balance` | `uint256` | The `wearer`'s balance of the Hat tokens. Can never be > 1. |

#### \_mintHat

Internal call to mint a Hat token to a wearer

_Unsafe if called when `_wearer` has a non-zero balance of `_hatId`_

```solidity
function _mintHat(address _wearer, uint256 _hatId) internal;
```

**Parameters**

| Name      | Type      | Description                                                       |
| --------- | --------- | ----------------------------------------------------------------- |
| `_wearer` | `address` | The wearer of the Hat and the recipient of the newly minted token |
| `_hatId`  | `uint256` | The id of the Hat to mint                                         |

#### \_burnHat

Internal call to burn a wearer's Hat token

_Unsafe if called when `_wearer` doesn't have a zero balance of `_hatId`_

```solidity
function _burnHat(address _wearer, uint256 _hatId) internal;
```

**Parameters**

| Name      | Type      | Description                                 |
| --------- | --------- | ------------------------------------------- |
| `_wearer` | `address` | The wearer from which to burn the Hat token |
| `_hatId`  | `uint256` | The id of the Hat to burn                   |

#### setApprovalForAll

Approvals are not necessary for Hats since transfers are not handled by the wearer

_Admins should use `transferHat()` to transfer_

```solidity
function setApprovalForAll(address, bool) public pure override;
```

#### safeTransferFrom

Safe transfers are not necessary for Hats since transfers are not handled by the wearer

_Admins should use `transferHat()` to transfer_

```solidity
function safeTransferFrom(address, address, uint256, uint256, bytes calldata) public pure override;
```

#### safeBatchTransferFrom

Safe transfers are not necessary for Hats since transfers are not handled by the wearer

```solidity
function safeBatchTransferFrom(address, address, uint256[] calldata, uint256[] calldata, bytes calldata)
    public
    pure
    override;
```

#### supportsInterface

ERC165 interface detection

_While Hats Protocol conforms to the ERC1155 interface, it does not fully conform to the ERC1155 specification since it does not implement the ERC1155Receiver functionality. For this reason, this function overrides the ERC1155 implementation to return false for ERC1155._

```solidity
function supportsInterface(bytes4 interfaceId) public pure override returns (bool);
```

**Parameters**

| Name          | Type     | Description                                       |
| ------------- | -------- | ------------------------------------------------- |
| `interfaceId` | `bytes4` | The interface identifier, as specified in ERC-165 |

**Returns**

| Name     | Type   | Description                                                            |
| -------- | ------ | ---------------------------------------------------------------------- |
| `<none>` | `bool` | bool True if the contract implements `interfaceId` and false otherwise |

#### balanceOfBatch

Batch retrieval for wearer balances

_Given the higher gas overhead of Hats balanceOf checks, large batches may be high cost or run into gas limits_

```solidity
function balanceOfBatch(address[] calldata _wearers, uint256[] calldata _hatIds)
    public
    view
    override(ERC1155, IHats)
    returns (uint256[] memory balances);
```

**Parameters**

| Name       | Type        | Description                                                  |
| ---------- | ----------- | ------------------------------------------------------------ |
| `_wearers` | `address[]` | Array of addresses to check balances for                     |
| `_hatIds`  | `uint256[]` | Array of Hat ids to check, using the same index as \_wearers |

#### uri

View the uri for a Hat

```solidity
function uri(uint256 id) public view override(ERC1155, IHats) returns (string memory _uri);
```

**Parameters**

| Name | Type      | Description       |
| ---- | --------- | ----------------- |
| `id` | `uint256` | The id of the Hat |

**Returns**

| Name   | Type     | Description                    |
| ------ | -------- | ------------------------------ |
| `_uri` | `string` | An 1155-compatible JSON object |

### Structs

#### Hat

This contract's version is labeled v1. Previous versions labeled similarly as v1 and v1.0 are deprecated, and should be treated as beta deployments.

A Hat object containing the hat's properties

_The members are packed to minimize storage costs_

```solidity
struct Hat {
    address eligibility;
    uint32 maxSupply;
    uint32 supply;
    uint16 lastHatId;
    address toggle;
    uint96 config;
    string details;
    string imageURI;
}
```
