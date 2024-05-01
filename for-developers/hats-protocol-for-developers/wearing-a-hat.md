---
description: >-
  The wearer of a given hat is assigned the responsibilities, authorities, and
  accountabilities associated with the hat.
---

# Wearing a Hat

An account's status relating to a given hat is determined by three factors. If all three are true, then the account is wearing the hat.

1. Whether their address has a balance of the Hat's token — we refer to this as the "static" balance
2. Whether the Hat is active (see the [Toggle section](toggle-modules.md) for more detail)
3. Whether they are eligible (see the [Eligibility section](eligibility-modules.md) for more detail)

Wearing a hat is a binary state. If all three of the above factors are true for a given account, then that account has a balance of 1 of that hat's id. If not, its balance is 0. It is not possible for any account to have a balance greater than 1 for any hat.

Hats Protocol has an [`isWearerOfHat()`](../v1-protocol-spec/interfaces/ihats.sol.md#iswearerofhat) convenience function that wraps `balanceOf()` and returns a bool for `balance == 1`.

### Dynamic hat balances

In Hats Protocol, the `balanceOf()` function does not simply reflect static contract storage — i.e., (1) from the above section. In addition, it reads (via a `staticcall`) dynamically from the hat's Eligibility and Toggle modules — (2) and (3) from above — and combines the three factors to arrive at the answer of whether a given address has a balance.

This design ensures that there is never a lame duck period between when a wearer's hat is revoked and when they actually lose the onchain authorities associated with the hat.&#x20;

However, since hat balances may change without an event — e.g., if the hat status flips from active to inactive based on an expiration-driven Toggle module — apps relying on indexed events may not be reading the source of truth.&#x20;

In such cases, there are two solutions:

1. Read directly from the contract — i.e., [`isWearerOfHat()`](../v1-protocol-spec/interfaces/ihats.sol.md#iswearerofhat)
2. Trigger a contract state change by calling [`checkHatWearerStatus()`](../v1-protocol-spec/interfaces/ihats.sol.md#checkhatwearerstatus) and/or [`checkHatStatus()`](../v1-protocol-spec/interfaces/ihats.sol.md#checkhatstatus)

### Who can wear a hat?

Any account can wear a hat, including:

* Externally Owned Accounts (EOAs)
* Logic contracts (i.e., contracts with explicit logic codified within functions), or
* Governance contracts (e.g., DAOs, multisigs, etc.)

Some of the most power applications of Hats Protocol are made possible by smart contracts wearing hats to automate or minimize trust required for certain logic.
