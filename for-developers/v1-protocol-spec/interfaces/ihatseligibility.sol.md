# IHatsEligibility.sol

## IHatsEligibility

[Git Source](https://github.com/Hats-Protocol/hats-protocol/blob/b43ad0d1dbe4a4190febc036ee8a2849e3f221b4/src/Interfaces/IHatsEligibility.sol)

### Functions

#### getWearerStatus

Returns the status of a wearer for a given hat

_If standing is false, eligibility MUST also be false_

```solidity
function getWearerStatus(address _wearer, uint256 _hatId) external view returns (bool eligible, bool standing);
```

**Parameters**

<table><thead><tr><th width="162.66666666666666">Name</th><th>Type</th><th>Description</th></tr></thead><tbody><tr><td><code>_wearer</code></td><td><code>address</code></td><td>The address of the current or prospective Hat wearer</td></tr><tr><td><code>_hatId</code></td><td><code>uint256</code></td><td>The id of the hat in question</td></tr></tbody></table>

**Returns**

<table><thead><tr><th width="166.66666666666666">Name</th><th width="247">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>eligible</code></td><td><code>bool</code></td><td>Whether the _wearer is eligible to wear the hat</td></tr><tr><td><code>standing</code></td><td><code>bool</code></td><td>Whether the _wearer is in goog standing</td></tr></tbody></table>
