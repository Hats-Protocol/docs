# Creating Hats

The creator of a hat must be its admin. In other words, the admin of a hat must be the `msg.sender` of the `Hats.createHat` function call. Though remember, by delegating its authority to a hatter contract, an admin can enable eligible others to create Hats based on whatever logic it desires.

Creating a Top Hat (a hat that serves as its own admin) requires a special function `mintTophat`, which creates a new hat, sets that hat as its own admin, and then mints its token to a `_target`. Any address wanting to create a hat that is not already wearing an admin hat of some kind must first create a Top Hat with itself as the wearer.

#### **Batch Creation**

In some scenarios, a DAO may want to create many hats at once -- including an entire hat tree -- at once. This is particularly useful when setting up an initial structure for a DAO or working group (e.g., from a hats template) or when forking an existing Hats structure from a template.

Enabling this latter forking/exit scenario is an important protection for hat wearers against potential abuse of power by their DAO.

To create a batch of hats, a DAO can call the `Hats.batchCreateHats()` function. This function takes arrays as its arguments, from which it constructs multiple hats. As long as each of these hats is part of the same tree of hats — i.e., they either have the same existing Hat or any of the newly created hats as admin(s) — they can all be created together.
