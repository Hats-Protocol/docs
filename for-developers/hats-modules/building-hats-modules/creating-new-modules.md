# Creating New Modules

### Getting Started

The [hats-module-template](https://github.com/Hats-Protocol/hats-module-template) repository makes it easy to get started building a new module. It has everything you need, including:

* An initialized Foundry project with a Hats-relevant config.
* Initial dependencies added: `forge-std` and `hats-module`.
* A stubbed out starter module contract.
* Test & deployment files boilerplate.
* Github CI workflows for Forge tests and gas cost diffs.

For eligibility modules, import and inherit from the [HatsEligibilityModule](https://github.com/Hats-Protocol/hats-module/blob/main/src/HatsEligibilityModule.sol) contract, which inherits from HatsModule and additionally implements the [IHatsEligibility](../../v1-protocol-spec/interfaces/ihatseligibility.sol.md) interface:

```solidity
import { HatsEligibilityModule } from "hats-module/HatsModule.sol";
```

Similarly, for toggle modules, import and inherit from the [HatsToggleModule](https://github.com/Hats-Protocol/hats-module/blob/main/src/HatsToggleModule.sol) contract, which inherits from HatsModule and additionally implements the [IHatsToggle](../../v1-protocol-spec/interfaces/ihatstoggle.sol.md) interface:

```solidity
import { HatsToggleModule } from "hats-module/HatsModule.sol";
```

### Best Practices

For compatibility with [module chains](../../building-hats-modules/about-module-chains.md), it is strongly recommended to adhere to the following practices:

#### Pull, don't push

Avoid pushing hat or hat wearer status directly to the protocol, i.e. via `IHats.setHatStatus` or `IHats.setHatWearerStatus`. These functions are only authorized to contracts set directly on the given hat as the toggle or eligibility module, respectively. Those calls would therefore revert when called from a module in a chain.

The simplest alternative is to not force the protocol to recognize any status updates, just let it pull them in dynamically the next time they are checked.

If you must have the protocol immediately recognize a new status, have the protocol pull the updates, ie via `IHats.checkHatStatus` or `IHats.checkHatWearerStatus`. These are fully public functions that will trigger the protocol to pull the current status from the modules set on the hat; if that's a chain, it will read from all the modules in the chain.

#### Don't force claiming

Some eligibility modules (such as [agreement-eligibility.md](../../../hats-integrations/eligibility-and-accountability-criteria/agreement-eligibility.md "mention") and [staking-eligibility.md](../../../hats-integrations/eligibility-and-accountability-criteria/staking-eligibility.md "mention")) include an option for would-be-wearers to [claim the hat](../../v1-sdk/core/claiming-hats.md) at the same time as they take an action to become eligible (e.g., signing the agreement and staking, respectively).

When building such a module, avoid _requiring_ that would-be-wearers claim the hat at the same time as taking the action to become eligible. Instead, give them an option to take the qualifying action independently, as well as bundled with claiming. _This will allow your module to work properly even when chained with another module that uses the qualifying action + claim approach_.

This is necessary because of the way the protocol handles minting when an eligibility module is attached to the hat. With a module attached, the protocol will only allow the hat to be minted if the recipient wearer is "explicitly eligible," i.e. eligible according to the module. In the case of a module chain, this will include eligibility information from all the modules in the chain, and so the would-be wearer may not be eligible for the hat as a whole even after they execute the qualifying action for one of its chained modules.

### Learn From Examples

To learn more and get inspiration, check out the awesome module that are already here:

* [Eligibility Modules](../../../hats-integrations/eligibility-and-accountability-criteria/#existing-modules)
* [Toggle Modules](../../../hats-integrations/activation-and-deactivation-criteria/#existing-modules)
* [Hatter Modules](../../../hats-integrations/hatter-modules/#existing-modules)
