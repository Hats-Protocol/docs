# How Module Instances Are Deployed

All contracts that inherit from [HatsModule](https://github.com/Hats-Protocol/hats-module/blob/main/src/HatsModule.sol) can be deployed as minimal proxy clones via [HatsModuleFactory](https://github.com/Hats-Protocol/hats-module/blob/main/src/HatsModuleFactory.sol), which offers several operations:

* create a single module instance
* batch create multiple module instances
* predict the address of a module instance
* check if a module instance has already been deployed

Each of these functions can be called directly on the HatsModuleFactory contract, or they can be accessed via the [Modules SDK](../modules-sdk/) to easily deploy new module instances and more.

### Create New Instance

The [createHatsModule](https://github.com/Hats-Protocol/hats-module/blob/5a69da357e70cc2e3727d6ec02097711439ec32b/src/HatsModuleFactory.sol#L69) function deploys a new proxy instance, for the provided implementation, to a deterministic address. The instance's immutable arguments are set its creation, and then `instance.setUp` is called with the provided initialization data.

```solidity
function createHatsModule(
    address _implementation,
    uint256 _hatId,
    bytes calldata _otherImmutableArgs,
    bytes calldata _initData
) public returns (address _instance)
```

_Parameters:_

* `_implementation` - The address of the implementation contract for which to deploy a clone.
* `_hatId` - The hat for which to deploy the module.
* `_otherImmutableArgs`: Immutable arguments to pass to the clone, packed encoded (via `abi.encodePacked`). These are additional to the ones [already included in HatsModule](inside-a-hats-module/#immutable-arguments).
* `_initData` - Encoded data (via abi.encode) to pass to the `setUp` function of the new instance.

_Returns_:

* `_instance` - The new instance's address.

_Events_:

Once the new module deployment and setup have completed, the function will emit the following event, which contains the new instance address:

```solidity
event HatsModuleFactory_ModuleDeployed(
    address implementation, address instance, uint256 hatId, bytes otherImmutableArgs, bytes initData
);
```

### Batch Create Multiple Instances

The [batchCreateHatsModule](https://github.com/Hats-Protocol/hats-module/blob/5a69da357e70cc2e3727d6ec02097711439ec32b/src/HatsModuleFactory.sol#L106) function creates multiple instances, using the [createHatsModule](how-module-instances-are-deployed.md#create-new-instance) function.&#x20;

The necessary creation parameters are passed as arrays, which must have the same length, equal to the number of modules to be created. For each module, the `createHatsModule` function will be called with the arrays entries, on the same corresponding index.

```solidity
function batchCreateHatsModule(
    address[] calldata _implementations,
    uint256[] calldata _hatIds,
    bytes[] calldata _otherImmutableArgsArray,
    bytes[] calldata _initDataArray
) public returns (bool success)
```

_Parameters:_

* `_implementations` - The addresses of the implementation contracts for which to deploy a clone.
* `_hatIds` - The hats for which to deploy the modules.
* `_otherImmutableArgsArray`: Immutable argumentss to pass to the clones, packed encoded (via `abi.encodePacked`). These are additional to the ones [already included in HatsModule](inside-a-hats-module/#immutable-arguments).
* `_initDataArray` - Encoded data (via abi.encode) to pass to the `setUp` function of each new module instance.

_Returns_:

* `success` - `True` if all modules were successfully created and initialized, `false` otherwise.

_Events_:

For every successfully created module, the function will emit the following event, which contains the new instance address:

```solidity
event HatsModuleFactory_ModuleDeployed(
    address implementation, address instance, uint256 hatId, bytes otherImmutableArgs, bytes initData
);
```

### Predict Module's Address

The [getHatsModuleAddress](https://github.com/Hats-Protocol/hats-module/blob/5a69da357e70cc2e3727d6ec02097711439ec32b/src/HatsModuleFactory.sol#L136) function predicts the address of a module instance before it was created.

```solidity
function getHatsModuleAddress(address _implementation, uint256 _hatId, bytes calldata _otherImmutableArgs)
    public
    view
returns (address)
```

_Parameters:_

* `_implementation` - The address of the implementation contract.
* `_hatId` - The hat for which to deploy a module.
* `_otherImmutableArgs`: Immutable arguments to pass to the clone, packed encoded (via `abi.encodePacked`). These are additional to the ones [already included in HatsModule](inside-a-hats-module/#immutable-arguments).

_Returns_:

* The predicted instance address.&#x20;

### Check If Deployed

The [deployed](https://github.com/Hats-Protocol/hats-module/blob/5a69da357e70cc2e3727d6ec02097711439ec32b/src/HatsModuleFactory.sol#L154) function checks if a certain module instance has been deployed.

```solidity
function deployed(address _implementation, uint256 _hatId, bytes calldata _otherImmutableArgs)
    public
    view
returns (bool)
```

_Parameters:_

* `_implementation` - The address of the implementation contract.
* `_hatId` - The hat for which to deploy a module.
* `_otherImmutableArgs`: Immutable arguments to pass to the clone, packed encoded (via `abi.encodePacked`). These are additional to the ones [already included in HatsModule](inside-a-hats-module/#immutable-arguments).

_Returns_:

* `True` if the instance has been deployed, `false` otherwise.&#x20;

### HatsModuleFactory Deployments

HatsModuleFactory [v0.6.0](https://github.com/Hats-Protocol/hats-module/releases/tag/v0.6.0) is deployed to the same address on all networks: 0xfE661c01891172046feE16D3a57c3Cf456729efA

It is known to have been deployed to the following networks:

* [Goerli testnet](https://goerli.etherscan.io/address/0xfE661c01891172046feE16D3a57c3Cf456729efA)
* [Ethereum Mainnet](https://etherscan.io/address/0xfE661c01891172046feE16D3a57c3Cf456729efA)
* [Optimism](https://optimistic.etherscan.io/address/0xfE661c01891172046feE16D3a57c3Cf456729efA)
* [Gnosis Chain](https://gnosisscan.io/address/0xfE661c01891172046feE16D3a57c3Cf456729efA)
* [Polygon](https://polygonscan.com/address/0xfe661c01891172046fee16d3a57c3cf456729efa)
* [Arbitrum](https://arbiscan.io/address/0xfe661c01891172046fee16d3a57c3cf456729efa)
