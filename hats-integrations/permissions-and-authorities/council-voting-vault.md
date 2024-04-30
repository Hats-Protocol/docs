---
description: >-
  How to only allow specified hats (or hats of a certain type) to vote in a
  Council voting vault
---

# Council Voting Vault

As the [Council Kit](https://blog.element.fi/launching-council-kit/) has gained adoption, we have heard the following needs from Council users:

1. **How can we create a more flexible system that allows members to vote in the way that best suits their needs?** Manually allow-listing members' addresses in a Council voting vault limits their optionality for how they may vote (e.g., if a DAO's contract address is listed as a Council member, they are unable to vote in any manner other than a full DAO vote).
2. **How can we make membership in a Council more legible and mutually-confirmed?** Denoting membership in a Council only by the inclusion of addresses in the voting vault lacks legibility and could be done without a member's consent.
3. **How can we streamline the process of granting and revoking access to workspaces, communication channels, and forums for new and existing members of a Council?** Current methods require manual addition to each individual platform, which can be time-consuming and prone to error.

**To solve these issues, we built a** [**Hats-powered Council Voting Vault**](https://github.com/Hats-Protocol/highcouncil-hats-vault/blob/main/src/HatsHighCouncilVotingVault.sol)**.**

With a Hats-powered Council voting vault, members of a collective, including cross-chain collectives, have the ability to choose to vote using their DAO contract, delegate their vote to a specific multisig (e.g., their stewardship council), delegate their vote to an individual representative, **or even vote cross-chain** by issuing the voting rep hat to the DAO's cross-chain avatar contract on the Council network.

[The Hats-powered Council voting vault](https://github.com/Hats-Protocol/highcouncil-hats-vault/blob/main/src/HatsHighCouncilVotingVault.sol) can be configured to check if a voter is a valid voter on behalf of or as a Member DAO by verifying that they have a Hats token ID matching a particular pattern. [Since Hats token IDs are addressable](../../for-developers/hats-protocol-overview/hat-ids.md), we can know what that pattern will be ahead of time based on the structure of the Hats tree, so we only have to configure the voting vault once, and no changes to it will be required as new Member DAOs (up to 65k) are added.

Additionally, using Hats, active DAO members are clearly legible and confirmed onchain, as any Hats token can be renounced by its wearer.

_This integration is currently in beta. Contact us at support \[at] hatsprotocol \[dot] xyz if you want to explore this integration, or_ [_check out the Hats Council Voting Vault repo here_](https://github.com/Hats-Protocol/highcouncil-hats-vault/blob/main/src/HatsHighCouncilVotingVault.sol)_._
