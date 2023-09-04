# Inside a Hats Module

The [HatsModule](https://github.com/Hats-Protocol/hats-module/blob/main/src/HatsModule.sol) contract provides a basic and generic structure, which modules can inherit from and extend to support any specific use case.&#x20;

It serves 2 main purposes:

* Easy starting point for module developers.
* Unified structure and patterns for modules enable additional tools and apps in the Hats ecosystem to automatically discover and use any newly created modules.

The contract is structured as a minimal proxy (clone) contract, similar to the EIP-1167 clone but with the addition of immutable arguments (see minimal proxy implementation [here](https://github.com/Vectorized/solady/blob/6c54795ef69838e233020e9ab29f3f6288efdf06/src/utils/LibClone.sol)).

Following are its main components:

### Immutable Arguments

Immutable arguments are variables which are set at each module instance creation (via the HatsModuleFactory) and are then constant through out the instance's lifetime.&#x20;

Accessing these variables is significantly cheaper than accessing regular storage variables, and so using this kind of variables is recommended for any variables which can be defined once, during instance creation, and then stay constant.

HatsModule includes the following immutable arguments, which are then included in any inheriting module:

* The address of the implementation contract of which the instance is a clone.
* The Hats Protocol address (Hats.sol).
* The hat ID for which the instance has been deployed.

Modules can add extra arguments, according to their needs.&#x20;

HatsModule inherits from the [Clone contract](https://github.com/Vectorized/solady/blob/6c54795ef69838e233020e9ab29f3f6288efdf06/src/utils/Clone.sol), which provides utility functions for reading immutable arguments. These functions are then used to create a public getter for each variable:

```solidity
function IMPLEMENTATION() public pure returns (address) {
    return _getArgAddress(0);
}

function HATS() public pure returns (IHats) {
    return IHats(_getArgAddress(20));
}

function hatId() public pure returns (uint256) {
    return _getArgUint256(40);
}
```

Note that the immutable arguments of an instance are passed to the [createHatsModule](how-module-instances-are-deployed.md#create-new-instance) function in the factory, rather than to the instance's contract itself.&#x20;

### Module Setup

To setup a module instance at creation time (via the [HatsModuleFactory](how-module-instances-are-deployed.md)), a module can override the [\_setUp](https://github.com/Hats-Protocol/hats-module/blob/5a69da357e70cc2e3727d6ec02097711439ec32b/src/HatsModule.sol#L70) function:

```solidity
function _setUp(bytes calldata _initData) internal virtual { }
```

_Parameters:_

* `_initData` - encoded initialization data (via `abi.encode`).

The [`createHatsModule`](how-module-instances-are-deployed.md#create-new-instance) function on the factory will trigger a call to this function with the provided initialization data, which can be used to initialize mutable storage variables or any other use.

### Versioning

HatsModule includes only one storage variable, for versioning purpose:

```solidity
string public version_;
```

This is used only for the implementation contract. To get the version from a module instance (proxy), the [version](https://github.com/Hats-Protocol/hats-module/blob/5a69da357e70cc2e3727d6ec02097711439ec32b/src/HatsModule.sol#L56) function is used:

```solidity
function version() public view returns (string memory) {
    return HatsModule(IMPLEMENTATION()).version_();
}
```
