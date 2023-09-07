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

### Learn From Examples

To learn more and get inspiration, check out the awesome module that are already here:

* [Eligibility Modules](../../../hats-integrations/eligibility-modules/#existing-modules)
* [Toggle Modules](../../../hats-integrations/toggle-modules/#existing-modules)
* [Hatter Modules](../../../hats-integrations/hatter-modules/#existing-modules)
