# About Module Chains

What if you want an eligibility criteria to be a combination of conditions implemented in separate modules? For example, to be eligible, a person has to own a certain NFT (e.g. representing a DAO membership) and additionally win an election? That's exactly what the eligibilities/toggles chain modules are for.

[HatsEligibilitiesChain](https://github.com/Hats-Protocol/hats-module/blob/main/src/HatsEligibilitiesChain.sol) is an eligibility module that composes any amount of eligibility modules with "and"/"or" logical operations. Similarly, [HatsTogglesChain](https://github.com/Hats-Protocol/hats-module/blob/main/src/HatsTogglesChain.sol) is a toggle module that composes any amount of toggle modules.

Both of these modules have a similar structure. Modules are chained in a format of a disjunction of conjunction clauses. For example, "(module1 && module2) || module3" has 2 conjunction clauses:&#x20;

1. "(module1 && module2)
2. "module3"&#x20;

These clauses are chained together with an "or" operation.&#x20;

**Deriving Wearer Eligibility:**

For the eligibilities chain module, a wearer's eligibility is derived by checking eligibility in each module and combining the results according to the chosen logical operations. However, if a wearer is in a bad standing according to any one of the modules, then the module will return a result of "not eligible" and "is in bad standing".

**Deriving Hat Status:**

For the toggles chain module, a hat's status is derived by checking it's status in each module and combining the results according to the chosen logical operations.&#x20;

### Create New Eligibilities/Toggles Chain Module

The module does not use any mutable storage variables and does not use initialization data. It only uses the following immutable variables, which are set at the module instance's creation time:

1. Number of conjunction clauses.
2. Conjunction clauses lengths.
3. The list of eligibility/toggle modules.

Using the example above, here's an example immutable arguments that will be used for the module's deployment:

```solidity
bytes memory otherImmutableArgs = abi.encodePacked(2, [2,1], module1Address, module2Address, module3Address);
```

The module includes the following getters for these immutable variables:

```solidity
function NUM_CONJUCTION_CLAUSES() public pure returns (uint256)

function CONJUCTION_CLAUSE_LENGTHS() public pure returns (uint256[] memory)

function MODULES() public pure returns (address[] memory)

```
