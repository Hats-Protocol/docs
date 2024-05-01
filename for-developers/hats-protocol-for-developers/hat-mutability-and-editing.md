# Hat Mutability and Editing

In some cases, a hat's properties should be immutable to give everybody (particularly the wearer(s)) maximal confidence in what they are signing up for. But this certainty comes at the expense of flexibility, which is often valuable for DAOs as they evolve and learn more about what their various roles are all about. With this trade-off in mind, Hats can be created as either mutable or immutable.

An **immutable** hat cannot be changed at all once it has been created. A **mutable** hat can be changed after it has been created. Only its admin(s) can make the change.

Changes are allowed to the following Hat properties:

* `details`
* `maxSupply` - as long as the new maxSupply is not less than the current supply
* `eligibility`
* `toggle`
* `mutable` - this is a one-way change
* `imageURI`

Additionally, mutable hats can be transferred by their admins to a different wearer. Immutable hats cannot be transferred.

### **Top Hat Exception**

The only exception to the above mutability rules is for Top Hats, which despite being immutable are allowed to change their own `details` and `imageURI` (but not other properties).

Note that this only includes non-linked Top Hats; a Top Hat that has been linked (aka grafted) onto another hat tree is no longer considered a Top Hat, and therefore is subject to the same mutability rules as other hats.
