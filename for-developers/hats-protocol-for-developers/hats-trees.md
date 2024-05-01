# Hats Trees

The fact that all hat's have hats as admins means that every hat exist within a "tree" of hats. This tree structure forms the basis for an organization's hats

Within a given branch of a hat tree, hats closer to the root of the tree have admin authorities for hats further down the branch. This is consistent with the direction of delegation of authority for DAOs, and combats the tendency for accountability to dilute as delegated authorities reach the edges of a network.

### **Top Hats**

Top Hats are the one exception to the rule that a hat's admin must be another hat. A Top Hat is a hat that serves as its own admin.

The root of a Hat tree is always a Top Hat. Typically, a DAO will wear the Top Hat that serves as admin for the tree of Hats related to the DAO's operations.

### Hat Trees and Hat Ids

Each hat tree has a max depth of 15 and a branching factor of 2^16. This means that each hat can have up to 2^16 = 65,536 children, and this pattern can repeat 14 times.

Every hat's id includes the id of its tree and its location within the tree. See the following page for more detail on [hat ids](hat-ids.md).
