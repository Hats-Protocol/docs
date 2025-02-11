---
description: This page describes the second version of Hats Signer Gate.
---

# 🔏 Hats Signer Gate v2

Hats Signer Gate (HSG) v2 is a contract that grants multisig signing rights to addresses wearing a given hats, enabling on-chain organizations to revocably delegate to individuals constrained authority and responsibility to operate an account (i.e. a Safe) owned by the organization.

### **Zodiac Module**

[HatsSignerGate.sol](https://github.com/hats-protocol/hats-zodiac) is a [Zodiac](https://github.com/gnosisguild/zodiac) **module** that...

1. Grants multisig signing rights to addresses based on whether they are wearing the appropriate Hat(s).
2. Removes signers who are no long valid (i.e. no longer wearing the signer Hat)
3. Manages the multisig threshold within the owner-specified range as new signers are added or removed.

### **Zodiac Guard**

Since Hat-wearing is dynamic — Hats can be programmatically revoked from wearers — this contract also services as a [Zodiac](https://github.com/gnosisguild/zodiac) **guard** to ensure that:

A) **Only valid signers can execute transactions**, i.e. only signatures made by accounts currently wearing a valid signer Hat count towards the threshold.

B) **Signers cannot execute transactions that remove the constraint in (A)**. Specifically, this contract guards against signers...

1. Executing _calls_ to the Safe itself. This prevents the signers from changing any of the Safe's storage values, including those referenced below.
2. Executing _delegatecalls_ to any [target contract](hats-signer-gate-v2.md#delegatecall-targets) not approved by the HSG owner
3. Executing any delegatecall (even to an approved target contract) that does the any of following
   1. Removes HSG as a guard on the Safe
   2. Removes HSG as a module on the Safe — or changing/adding any other modules
   3. Changes the Safe threshold
   4. Changes the Safe owners (aka signers)
   5. Changes the Safe fallback handler

{% hint style="warning" %}
Protections against (3c) and (3d) above only hold if the Safe does not have any authority over the signer Hat(s). If it does — e.g. it wears an admin Hat of the signer Hat(s) or is an eligibility or toggle module on the signer Hat(s) — then in some cases the signers may be able to indirectly change the Safe threshold or owners.

Proceed with caution if granting such authority to a Safe attached to HatsSignerGate.
{% endhint %}

### Signer Management

Hats Signer Gate provides several ways to manage Safe signers based on their hat-wearing status:

#### **Claiming Signer Rights**

* Individual hat wearers can claim their own signing rights via `claimSigner()`
* Must be wearing a valid signer hat at time of claim
* Each signer's hat ID is registered and tracked for future validation

#### **Claiming for Others**

When enabled by the owner (`claimableFor = true`):

* Anyone can claim signing rights on behalf of valid hat wearers via `claimSignerFor()` or `claimSignersFor()`
* Useful for batch onboarding of signers
* Prevents re-registration if signer is still wearing their currently registered hat

#### **Signer Removal**

* Signers who no longer wear their registered hat can be removed via `removeSigner()`
* Threshold automatically adjusts according to the threshold configuration
* If the removed signer was the last valid signer, the contract itself becomes the sole owner

### Threshold Configuration

The threshold (number of required signatures) is managed dynamically based on the `ThresholdConfig`:

#### **Threshold Types**

1. **ABSOLUTE**
   * Sets a fixed target number of required signatures
   * Example: Always require exactly 3 signatures
   * Bounded by min threshold and number of valid signers
2. **PROPORTIONAL**
   * Sets a percentage of total signers required (in basis points)
   * Example: Require 51% of signers (5100 basis points)
   * Actual number of required signatures rounds up
   * Still bounded by min threshold

#### **Configuration Parameters**

* `min`: Minimum number of required signatures (must be > 0)
* `target`: Either fixed number (ABSOLUTE) or percentage in basis points (PROPORTIONAL)
* `thresholdType`: ABSOLUTE (0) or PROPORTIONAL (1)

The Safe's threshold is automatically adjusted when:

* New signers are added
* Existing signers are removed
* Threshold configuration is changed

### Delegatecall Targets

HSG restricts delegatecalls to protect the Safe from unauthorized modifications. Only approved targets can receive delegatecalls.

**Default Enabled Targets**

The following MultiSend libraries are enabled by default:

<table><thead><tr><th>Address</th><th width="118">Version</th><th width="100">Type</th></tr></thead><tbody><tr><td><code>0x40A2aCCbd92BCA938b02010E17A5b8929b49130D</code></td><td>v1.3.0</td><td>canonical</td></tr><tr><td><code>0xA1dabEF33b3B82c7814B6D82A79e50F4AC44102B</code></td><td>v1.3.0</td><td>eip155</td></tr><tr><td><code>0x9641d764fc13c8B624c04430C7356C1C7C8102e2</code></td><td>v1.4.1</td><td>canonical</td></tr></tbody></table>

See [safe-deployments](https://github.com/safe-global/safe-deployments/tree/main/src/assets) for more information.

### **Security Considerations**

* Delegatecalls can modify Safe state if not properly restricted. Owners should NOT approve delegatecall targets that enable the following:
  * Directly modifying any of the Safe's state, including the Safe's nonce.
  * Additional delegatecalls. For example, the [MultiSend.sol](https://github.com/safe-global/safe-smart-account/blob/v1.4.1-3/contracts/libraries/MultiSend.sol) library that is _not_ "call only" should not be approved. The [MultiSendCallOnly.sol](https://github.com/safe-global/safe-smart-account/blob/v1.4.1-3/contracts/libraries/MultiSendCallOnly.sol) is approved by default.
* HSG validates that approved delegatecalls don't modify critical Safe parameters, but relies on the Safe' nonce to do so.
* Direct calls to the Safe are always prohibited
* When detaching HSG from a Safe — i.e. when calling `detach()` — the owner must trust that admin(s) of the signer Hat(s) will not front-run the detachment to add arbitrary signers. Since admins in Hats Protocol are already trusted (and can be revoked, held accountable, etc.) this is not an additional risk, but HSG owners should nonetheless be aware of this risk.

### Contract Ownership

The wearer of the `ownerHat` can make the following changes to Hats Signer Gate:

1. "Transfer" ownership to a new Hat by changing the `ownerHat`
2. Change the threshold configuration
3. Enable other Zodiac modules on HSG itself
4. Enable another Zodiac guard on HSG itself
5. Add other Hats as valid signer Hats
6. Enable or disable the ability for others to claim signer rights on behalf of valid hat wearers (`claimableFor`)
7. Detach HatsSignerGate from the Safe (removing it as both guard and module)
8. Migrate to a new HatsSignerGate instance
9. Enable or disable specific delegatecall targets
10. Lock the contract permanently, preventing any further owner changes

### Deploying New Instances

Instances of HSG can be created via the [Zodiac module proxy factory](https://github.com/gnosisguild/zodiac/blob/18b7575bb342424537883f7ebe0a94cd7f3ec4f6/contracts/factory/ModuleProxyFactory.sol).

Instances can be created for an existing Safe by passing the Safe address on initialization, or for a new Safe to be deployed from within HSG's initialization.

### Security Audits

v2 — the present version — has received the following security audits. See the v2 audits directory for the detailed reports.

| Auditor  | Report Date       | Commit Hash                                                                                             | Notes                     |
| -------- | ----------------- | ------------------------------------------------------------------------------------------------------- | ------------------------- |
| Sherlock | December 13, 2024 | [a9e3f4f](https://github.com/Hats-Protocol/hats-zodiac/commit/a9e3f4f0e968fb332800a468eddcb993fc6d5cd2) | 166 auditors participated |

{% hint style="info" %}
Since this audit was completed, HSG code was updated to add a variable salt to the Safe proxy creation within the `SafeManagerLib.deploySafeAndAttachHSG` function. This ensures that the address of the Safe proxy is unique to the HSG instance.
{% endhint %}

### Recent Deployments

See [Releases](https://github.com/Hats-Protocol/hats-zodiac/releases) for deployments. Specific deployment parameters are stored here.
