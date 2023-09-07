# Immutable Arguments

Immutable arguments are variables which are set at each module instance creation (via the HatsModuleFactory) and are then constant through out the instance's lifetime.&#x20;

Accessing these variables is significantly cheaper than accessing regular storage variables, and so using this kind of variables is recommended for any variables which can be defined once, during instance creation, and then stay constant.

### Standard HatsModule Immutable Args

HatsModule includes several immutable arguments as standard, which are then included in any inheriting module.&#x20;

* `IMPLEMENTATION`: The address of the implementation contract of which the instance is a clone.
* `HATS`: The Hats Protocol address (Hats.sol).
* `hatId`: The hat ID for which the instance has been deployed. This can be utilized in various ways depending on the module's use case.

### Immutable Arg "Storage"

LibClone.sol handles "storage" of these values in the instance's bytecode, with the following layout:

<table><thead><tr><th width="105">Offset</th><th>Constant</th><th width="111">Type</th><th width="115">Length</th><th>Source</th></tr></thead><tbody><tr><td>0</td><td>IMPLEMENTATION</td><td>address</td><td>20</td><td>HatsModule</td></tr><tr><td>20</td><td>HATS</td><td>address</td><td>20</td><td>HatsModule</td></tr><tr><td>40</td><td>hatId</td><td>address</td><td>32</td><td>HatsModule</td></tr><tr><td>[72+]</td><td>[other args]</td><td>[type]</td><td>[len]</td><td>[your module]</td></tr></tbody></table>

Each is accessible by a pure function based on utility functions from LibClone.sol.

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

### Custom Immutable Arguments

Modules can include as many additional immutable arguments as they need, and each can be made accessible by similar pure functions.

Note that the immutable arguments of an instance are passed to the [createHatsModule](../how-module-instances-are-deployed.md#create-new-instance) function in the factory, rather than to the instance's contract itself. See the next section for more details on how that works.
