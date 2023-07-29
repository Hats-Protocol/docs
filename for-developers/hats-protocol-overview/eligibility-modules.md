# Eligibility Modules

Eligibility modules have authority to rule on the a) eligibility and b) good standing of wearer(s) of a given hat.

**Wearer Eligibility** (A) determines whether a given address is eligible to wear the hat. This applies both before and while the address wears the hat. Consider the following scenarios for a given address:

|                             | Eligible                         | Not Eligible                        |
| --------------------------- | -------------------------------- | ----------------------------------- |
| **Doesn't wear the Hat**    | Hat can be minted to the address | Hat cannot be minted to the address |
| **Currently wears the Hat** | Keeps wearing the hat            | The hat is revoked                  |

When a hat is revoked, its token is burned.

**Wearer Standing** (B) determines whether a given address is in good or bad standing. Standing is stored on-chain in `Hats.sol` to facilitate accountability.

For example, a hatter contract implementing staking logic could slash a wearer's stake if they are placed in bad standing by the eligibility module.

An address placed in bad standing by a hat's eligibility module automatically loses eligibility for that hat. Note, though, that ineligibility does necessarily imply bad standing; it is possible for an address may be ineligible but in good standing.

Any address can serve as an eligibility module for a given hat. Hats Protocol supports two categories of eligibility modules:

1. **Mechanistic eligibility** are logic contracts that implement the `IHatsEligibility` interface, which enables the Hats.sol contract to _pull_ wearer standing by calling `checkWearerStanding` from within the `Hats.balanceOf` function. Mechanistic eligibility enables instantaneous revocation based on pre-defined triggers.
2. **Humanistic eligibility** are either EOAs or governance contracts. To revoke a Hat, humanistic eligibility must _push_ updates to the Hats contract by calling `Hats.ruleOHatWearerStanding`.

Unlike admins, eligibility modules are explicitly set as addresses, not hats. This is to avoid long, potentially illegible, chains of revocation authority that can affect wearer penalties (such as slashed stake).
