# HatsIdUtilities.sol

## HatsIdUtilities

[Git Source](https://github.com/Hats-Protocol/hats-protocol/blob/b43ad0d1dbe4a4190febc036ee8a2849e3f221b4/src/HatsIdUtilities.sol)

**Inherits:** IHatsIdUtilities

**Author:** Haberdasher Labs

_Functions for working with Hat Ids from Hats Protocol. Factored out of Hats.sol for easier use by other contracts._

### State Variables

#### linkedTreeRequests

Mapping of tophats requesting to link to admin hats in other trees

_Linkage only occurs if request is approved by the new admin_

```solidity
mapping(uint32 => uint256) public linkedTreeRequests;
```

#### linkedTreeAdmins

Mapping of approved & linked tophats to admin hats in other trees, used for grafting one hats tree onto another

_Trees can only be linked to another tree via their tophat_

```solidity
mapping(uint32 => uint256) public linkedTreeAdmins;
```

#### TOPHAT\_ADDRESS\_SPACE

Hat Ids serve as addresses. A given Hat's Id represents its location in its hat tree: its level, its admin, its admin's admin (etc, all the way up to the tophat). The top level consists of 4 bytes and references all tophats. Each level below consists of 16 bits, and contains up to 65,536 child hats. A uint256 contains 4 bytes of space for tophat addresses, giving room for ((256 - 32) / 16) = 14 levels of delegation, with the admin at each level having space for 65,536 different child hats. A hat tree consists of a single tophat and has a max depth of 14 levels.

_Number of bits of address space for tophat ids, ie the tophat domain_

```solidity
uint256 internal constant TOPHAT_ADDRESS_SPACE = 32;
```

#### LOWER\_LEVEL\_ADDRESS\_SPACE

_Number of bits of address space for each level below the tophat_

```solidity
uint256 internal constant LOWER_LEVEL_ADDRESS_SPACE = 16;
```

#### MAX\_LEVELS

_Maximum number of levels below the tophat, ie max tree depth (256 - TOPHAT\_ADDRESS\_SPACE) / LOWER\_LEVEL\_ADDRESS\_SPACE;_

```solidity
uint256 internal constant MAX_LEVELS = 14;
```

### Functions

#### buildHatId

Constructs a valid hat id for a new hat underneath a given admin

_Reverts if the admin has already reached `MAX_LEVELS`_

```solidity
function buildHatId(uint256 _admin, uint16 _newHat) public pure returns (uint256 id);
```

**Parameters**

| Name      | Type      | Description                         |
| --------- | --------- | ----------------------------------- |
| `_admin`  | `uint256` | the id of the admin for the new hat |
| `_newHat` | `uint16`  | the uint16 id of the new hat        |

**Returns**

| Name | Type      | Description            |
| ---- | --------- | ---------------------- |
| `id` | `uint256` | The constructed hat id |

#### getHatLevel

Identifies the level a given hat in its hat tree

```solidity
function getHatLevel(uint256 _hatId) public view returns (uint32 level);
```

**Parameters**

| Name     | Type      | Description                   |
| -------- | --------- | ----------------------------- |
| `_hatId` | `uint256` | the id of the hat in question |

**Returns**

| Name    | Type     | Description             |
| ------- | -------- | ----------------------- |
| `level` | `uint32` | (0 to type(uint32).max) |

#### getLocalHatLevel

Identifies the level a given hat in its local hat tree

_Similar to getHatLevel, but does not account for linked trees_

```solidity
function getLocalHatLevel(uint256 _hatId) public pure returns (uint32 level);
```

**Parameters**

| Name     | Type      | Description                   |
| -------- | --------- | ----------------------------- |
| `_hatId` | `uint256` | the id of the hat in question |

**Returns**

| Name    | Type     | Description                   |
| ------- | -------- | ----------------------------- |
| `level` | `uint32` | The local level, from 0 to 14 |

#### isTopHat

Checks whether a hat is a topHat

```solidity
function isTopHat(uint256 _hatId) public view returns (bool _isTopHat);
```

**Parameters**

| Name     | Type      | Description         |
| -------- | --------- | ------------------- |
| `_hatId` | `uint256` | The hat in question |

**Returns**

| Name        | Type   | Description                 |
| ----------- | ------ | --------------------------- |
| `_isTopHat` | `bool` | Whether the hat is a topHat |

#### isLocalTopHat

Checks whether a hat is a topHat in its local hat tree

_Similar to isTopHat, but does not account for linked trees_

```solidity
function isLocalTopHat(uint256 _hatId) public pure returns (bool _isLocalTopHat);
```

**Parameters**

| Name     | Type      | Description         |
| -------- | --------- | ------------------- |
| `_hatId` | `uint256` | The hat in question |

**Returns**

| Name             | Type   | Description                                    |
| ---------------- | ------ | ---------------------------------------------- |
| `_isLocalTopHat` | `bool` | Whether the hat is a topHat for its local tree |

#### isValidHatId

```solidity
function isValidHatId(uint256 _hatId) public pure returns (bool validHatId);
```

#### getAdminAtLevel

Gets the hat id of the admin at a given level of a given hat

_This function traverses trees by following the linkedTreeAdmin pointer to a hat located in a different tree_

```solidity
function getAdminAtLevel(uint256 _hatId, uint32 _level) public view returns (uint256 admin);
```

**Parameters**

| Name     | Type      | Description                   |
| -------- | --------- | ----------------------------- |
| `_hatId` | `uint256` | the id of the hat in question |
| `_level` | `uint32`  | the admin level of interest   |

**Returns**

| Name    | Type      | Description                       |
| ------- | --------- | --------------------------------- |
| `admin` | `uint256` | The hat id of the resulting admin |

#### getAdminAtLocalLevel

Gets the hat id of the admin at a given level of a given hat local to the tree containing the hat.

```solidity
function getAdminAtLocalLevel(uint256 _hatId, uint32 _level) public pure returns (uint256 admin);
```

**Parameters**

| Name     | Type      | Description                   |
| -------- | --------- | ----------------------------- |
| `_hatId` | `uint256` | the id of the hat in question |
| `_level` | `uint32`  | the admin level of interest   |

**Returns**

| Name    | Type      | Description                       |
| ------- | --------- | --------------------------------- |
| `admin` | `uint256` | The hat id of the resulting admin |

#### getTopHatDomain

Gets the tophat domain of a given hat

_A domain is the identifier for a given hat tree, stored in the first 4 bytes of a hat's id_

```solidity
function getTopHatDomain(uint256 _hatId) public pure returns (uint32 domain);
```

**Parameters**

| Name     | Type      | Description                   |
| -------- | --------- | ----------------------------- |
| `_hatId` | `uint256` | the id of the hat in question |

**Returns**

| Name     | Type     | Description                    |
| -------- | -------- | ------------------------------ |
| `domain` | `uint32` | The domain of the hat's tophat |

#### getTippyTopHatDomain

Gets the domain of the highest parent tophat — the "tippy tophat"

```solidity
function getTippyTopHatDomain(uint32 _topHatDomain) public view returns (uint32 domain);
```

**Parameters**

| Name            | Type     | Description                                   |
| --------------- | -------- | --------------------------------------------- |
| `_topHatDomain` | `uint32` | the 32 bit domain of a (likely linked) tophat |

**Returns**

| Name     | Type     | Description             |
| -------- | -------- | ----------------------- |
| `domain` | `uint32` | The tippy tophat domain |

#### noCircularLinkage

Checks For any circular linkage of trees

```solidity
function noCircularLinkage(uint32 _topHatDomain, uint256 _linkedAdmin) public view returns (bool notCircular);
```

**Parameters**

| Name            | Type      | Description                                |
| --------------- | --------- | ------------------------------------------ |
| `_topHatDomain` | `uint32`  | the 32 bit domain of the tree to be linked |
| `_linkedAdmin`  | `uint256` | the hatId of the potential tree admin      |

**Returns**

| Name          | Type   | Description                      |
| ------------- | ------ | -------------------------------- |
| `notCircular` | `bool` | circular link has not been found |

#### sameTippyTopHatDomain

Checks that a tophat domain and its potential linked admin are from the same tree, ie have the same tippy tophat domain

```solidity
function sameTippyTopHatDomain(uint32 _topHatDomain, uint256 _newAdminHat) public view returns (bool sameDomain);
```

**Parameters**

| Name            | Type      | Description                                  |
| --------------- | --------- | -------------------------------------------- |
| `_topHatDomain` | `uint32`  | The 32 bit domain of the tophat to be linked |
| `_newAdminHat`  | `uint256` | The new admin for the linked tree            |

**Returns**

| Name         | Type   | Description                                                                                          |
| ------------ | ------ | ---------------------------------------------------------------------------------------------------- |
| `sameDomain` | `bool` | Whether the \_topHatDomain and the domain of its potential linked \_newAdminHat domains are the same |
