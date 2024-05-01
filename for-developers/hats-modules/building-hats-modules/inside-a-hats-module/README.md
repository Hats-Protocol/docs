# Inside a Hats Module

Typically, Hats Modules inherit from the [HatsModule.sol](https://github.com/Hats-Protocol/hats-module/blob/main/src/HatsModule.sol) contract. This is an abstract contract that provides a generic structure that modules can extend to support any specific use case.

It serves several key functions:

1. Provide the basic boiler plate required for a new Hats module contract.
2. Enable compatibility with [HatsModuleFactory.sol](../how-module-instances-are-deployed.md), the easiest and cheapest way for users to deploy new instances of a given module.
3. Enable compatibility with the [module registry](https://github.com/Hats-Protocol/modules-registry), which facilitates user discovery and integration into Hats front ends.

{% hint style="info" %}
Inheriting from HatsModule.sol is necessary to be deployable via HatsModuleFactory, to be listed in the Module registry, and to appear natively in the applications using the registry.&#x20;

However, it is _not_ required for compatibility with Hats Protocol more generally. See the docs for [Eligibility](../../../hats-protocol-for-developers/eligibility-modules.md) and [Toggle](../../../hats-protocol-for-developers/toggle-modules.md) modules for those requirements.

The remainder of this documentation assumes inheritance of HatsModule.
{% endhint %}

## HatsModule.sol

HatsModule.sol's primary function is to enable a module to be configured and deployed via [HatsModuleFactory](../how-module-instances-are-deployed.md). Often, each new hat to which a module is attached involves a new instance of that module, so its important for deployment to be gas-efficient. Additionally, each module is likely to be called many times over its life, so its also important for runtime execution to be gas-efficient.&#x20;

For these reasons, HatsModule.sol is structured as a minimal proxy (clone) contract — similar to the [EIP-1167](https://eips.ethereum.org/EIPS/eip-1167) standard — that also supports immutable arguments. It implements the gas-efficient [LibClone.sol](https://github.com/Vectorized/solady/blob/6c54795ef69838e233020e9ab29f3f6288efdf06/src/utils/LibClone.sol) library.

See the following pages for more detail about how HatsModule.sol operates:

{% content-ref url="immutable-arguments.md" %}
[immutable-arguments.md](immutable-arguments.md)
{% endcontent-ref %}

{% content-ref url="module-setup.md" %}
[module-setup.md](module-setup.md)
{% endcontent-ref %}

{% content-ref url="versioning.md" %}
[versioning.md](versioning.md)
{% endcontent-ref %}

### Extensions

There are a couple stock extensions to HatsModule.sol that are useful starting points for common types of modules:

* HatsEligibilityModule.sol: implements [`IHatsEligibility.sol`](../../../hats-protocol-for-developers/eligibility-modules.md)
* HatsToggleModule.sol: implements [`IHatsToggle.sol`](../../../hats-protocol-for-developers/toggle-modules.md)

