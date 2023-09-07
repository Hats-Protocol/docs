# Module Setup

Each module instance is initialized at creation time by the public [setUp](https://github.com/Hats-Protocol/hats-module/blob/5a69da357e70cc2e3727d6ec02097711439ec32b/src/HatsModule.sol#L65) function, which is triggered by the [`createHatsModule`](../how-module-instances-are-deployed.md#create-new-instance)  function in [HatsModuleFactory](../how-module-instances-are-deployed.md). This is where custom initial (mutable) variables and other configurations are set.

That custom logic can be implemented in the virtual [\_setUp](https://github.com/Hats-Protocol/hats-module/blob/5a69da357e70cc2e3727d6ec02097711439ec32b/src/HatsModule.sol#L70) function, which the module implementation should override.

```solidity
function _setUp(bytes calldata _initData) internal virtual { }
```

_Parameters:_

* `_initData` - abi-encoded initialization data.

{% hint style="info" %}
The `setUp` function is modified by OpenZeppelin's [initializable](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/proxy/utils/Initializable.sol), which prevents any future calls that could re-initialize the instance. `setUp` will be called even if `_setUp` is empty, ensuring that all instances are properly initialized.
{% endhint %}
