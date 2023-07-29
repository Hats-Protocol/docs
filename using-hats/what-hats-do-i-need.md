# 👥 What Hats Do I Need?

Hats are roles, and roles are rich objects that compose a lot of things together, including: responsibilities, authorities, and accountabilities.

What roles might you want to represent as hats? As you consider all the hats you may want to deploy, it may be helpful to consider the following kinds of roles we commonly see embodied onchain as hats.

## Different Kinds of Roles

Hats can represent roles at different levels of granularity. It can be helpful to start broad and get increasingly granular, listing each hat as you go.

**The Top Hat:** The broadest authority of your Hats tree is represented by the Top Hat. This is the first hat you will create; you can think of it as the superadmin of the entire Hats tree. _Top Hats should be worn by the highest-level governance surface of your organization._ That said, when you're just getting started it's usually OK to first mint the Top Hat to an address you control and then transfer the Top Hat to the organization's address later.

**Workstream, Team, and Group Roles:** Next, consider the roles held collectively by a group, such as Councils, Workstreams, Guilds, and other organizational units. Any address can wear a hat, so multisigs and pods can and often should be represented by hats as well.

**Individual Roles:** What roles exist in your organization that will be held by individual people? Roles can be broad and held by many people, as in a Community Member Hat or Guild Member Hat, or narrow and specific, as in a Workstream Facilitator Hat or Recognized Delegate Hat. Roles may also be ongoing, or bound to a specific project or deliverable.

**Discrete Authorities:** Consider any granular authorities that should be represented by a hat to enable capture-resistant delegation and revocation of specific credentials. See the "Hat Authorities" section below for examples of the types of authorities that can be enabled by Hats.

**Claimable Hats:** By default, hats are only delegated, revoked, and renounced, but not claimed. However, it is possible to make designated hats claimable by adding a [ClaimsHatter Contract](https://github.com/Hats-Protocol/claims-hatter) Hat and making it an admin of any hats you want to be claimable ([see the guide for Making Hats Claimable here)](../hats-integrations/claiming-and-onboarding-integrations/making-hats-claimable.md). If you think you'll want some of your hats to be claimable, add a ClaimsHatter Contract Hat to your list.

Your Hats tree is meant to evolve with your organization, so don't feel pressure to get it perfect from the start. For example, roles can continue to be added, removed, and changed over time (as long as they are [mutable](setting-hat-properties.md#mutability)). The wearers of a given hat may change over time as well, as a given hat can be worn first by a single individual and later transferred to a group (e.g., a multisig or pod), or vice versa.
