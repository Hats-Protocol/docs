# 👥 What Hats Do I Need?

Hats are roles, and roles are rich objects that compose a lot of things together, including: responsibilities, authorities, and accountabilities.

What roles might you want to represent as hats? As you consider all the hats you may want to deploy, it may be helpful to consider the following kinds of roles we commonly see embodied onchain as hats.

## Different Kinds of Roles

Hats can represent roles at different levels of granularity. It can be helpful to start broad and get increasingly granular, listing each hat as you go.

### **The Top Hat**

The broadest authority of your Hats tree is represented by the Top Hat. This is the first hat you will create; you can think of it as the superadmin of the entire Hats tree. _Top Hats should be worn by the highest-level governance surface of your organization._ That said, when you're just getting started it's usually OK to first mint the Top Hat to an address you control and then transfer the Top Hat to the organization's address later.

### **Workstream, Team, and Group Roles**

Next, consider the roles held collectively by a group, such as Councils, Workstreams, Guilds, and other organizational units. Any address can wear a hat, so multisigs and pods can and often should be represented by hats as well.

### **Individual Roles**

What roles exist in your organization that will be held by individual people? Roles can be broad and held by many people, as in a Community Member Hat or Guild Member Hat, or narrow and specific, as in a Workstream Facilitator Hat or Recognized Delegate Hat. Roles may also be ongoing, or bound to a specific project or deliverable.

### **Discrete Authorities**

Consider any granular authorities that should be represented by a hat to enable capture-resistant delegation and revocation of specific credentials. See the [Hat-Gated Authorities](../hats-integrations/permissions-and-authorities/) section below for examples of the types of authorities that can be enabled by Hats.

Your Hats tree is meant to evolve with your organization, so don't feel pressure to get it perfect from the start. For example, roles can continue to be added, removed, and changed over time (as long as they are [mutable](setting-a-hats-basic-properties.md#editable-mutability)). The wearers of a given hat may change over time as well, as a given hat can be worn first by a single individual and later transferred to a group (e.g., a multisig or pod), or vice versa.

## General Recommendations

Here are some general recommendations for an organization's tree structure:

* The [Top Hat](what-hats-do-i-need.md#the-top-hat) wearer is the entity that represents the organization's highest-level governance surface.
* Right below the Top Hat, create an "Autonomous Admin" role, from which the rest of the tree will flow. This role can be granted to smart contracts that will automate certain operations, e.g. making other roles in the tree [claimable by eligible accounts](making-hats-claimable.md), and more. Creating this dedicated role will future-proof your tree for handling automation/operational needs.
* [Workstreams, Teams, or Groups](what-hats-do-i-need.md#workstream-team-and-group-roles) wear Level 2 hats (just below the Autonomous Admin).
* [Individual Role](what-hats-do-i-need.md#individual-roles) Hats and [Discrete Authority](what-hats-do-i-need.md#discrete-authorities) Hats are located at the lower-levels of the tree.

{% hint style="info" %}
The Autonomous Admin role can also enable an individual EOA to temporarily set up and manage the Hats tree for a period of time, usually during a bootstrap period.
{% endhint %}

<figure><img src="../.gitbook/assets/Screenshot 2024-04-10 at 12.58.39.png" alt=""><figcaption></figcaption></figure>
