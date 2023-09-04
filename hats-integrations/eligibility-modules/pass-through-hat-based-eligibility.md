# Pass-Through (Hat-Based) Eligibility

A Hats Protocol module that enables an authorized hat to serve as the eligibility and/or toggle module for other hat(s).

In Hats Protocol v1, eligibility and toggle modules are set as addresses. This creates a lot of flexibility, since addresses can be EOAs, multisigs, DAOs, or even other smart contracts. But hats themselves cannot be set explicitly as eligibility or toggle modules because hats are identified by a uint256 hatId, not an address.

Passthrough Module is a contract that can be set as the eligibility and/or toggle module for a target hat, and allows the wearer(s) of another hat to call the eligibility and/or toggle functions of the target hat. This allows hats themselves to be used as eligibility and toggle modules.

This contract is a "humanistic" module, not a "mechanistic" module. It does not inherit from `IHatsEligibility.sol` or `IHatsToggle.sol`, so Hats Protocol cannot pull any data from it. It serves only as a passthrough, enabling the wearer(s) of the authorized hat to push eligibility and toggle data about the target hat to Hats Protocol.

The module's code is open source and is available [here](https://github.com/Hats-Protocol/passthrough-modules).

## **Using the** Pass-Through **Eligibility Module**

_This eligibility module is currently in beta. Contact us at support \[at] hatsprotocol \[dot] xyz if you want to explore this module, or check out the_ Pass-Through eligibility _Github repo_ [_here_](https://github.com/Hats-Protocol/passthrough-modules)_._
