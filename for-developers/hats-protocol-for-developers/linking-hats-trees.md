# Linking Hats Trees

Not all Hats trees will unfurl from top down or inside out. Sometimes, new branches will form independently from the main tree, or multiple trees will form before a main tree even exists.

In these cases, Hats trees can be grafted onto other trees. This is done via a request-approve process where the wearer of one tree's Top Hat requests to link their Top Hat to a hat in another tree, whose admin can approve if desired. This has three main effects:

1. The linked Top Hat loses its Top Hat status (i.e., `Hats.isTopHat` will return `false`) and turns into what we call a "tree root" or "linked Top Hat", and
2. The hat to which it is linked becomes its new admin; it is no longer its own admin
3. On linking, the linked Top Hat can be assigned eligibility and/or toggle modules like any other hat

Linked hat trees can also be unlinked by the tree root from its linked admin, via `Hats.unlinkTopHatFromTree`. This causes the tree root to regain its status as a top hat and to once again become its own admin. Any eligibility or toggle modules added on linking are cleared. Note that unlinking is only allowed if the tree root is active and has an eligible wearer.

{% hint style="warning" %}
**CAUTION**: Be careful when nesting multiple Hat trees. If the nested linkages become too long, the higher level admins may lose control of the lowest level hats because admin actions at that distance may cost-prohibitive or even exceed the gas limit. Best practice is to not attach external authorities (e.g. via token gating) to hats in trees that are more than \~10 nested trees deep (varies by network).
{% endhint %}

### **Relinking**

A linked Top Hat can be relinked to a different hat within the same tree. This is useful for groups that want to reorganize their subtrees without having to go through the request and approve steps. Valid relinks must meet the following criteria in order to ensure security:

1. The hat wearer executing the relink is an admin of both the linked topHat and the new admin (destination)
2. The new admin (destination) is within the same local tree as the existing admin (origin), or within the Tippy Top Hat's local tree. Tippy Top Hats executing a relink are not subject to these restrictions.
3. The new link does not create a circular linkage.
