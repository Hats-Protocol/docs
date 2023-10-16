# 🧙 Admins: Creating, Issuing, and Revising Hats

In Hats Protocol, admins are specific hats that can change a child hat's details, image, max supply, eligibility address, and toggle address — as long as that child hat is mutable (immutable hats cannot be changed once deployed). Admin hats can also mint both mutable and immutable hats to new wearers, and transfer mutable hats from one address to another.

Each hat is an admin of all other hats linked directly below it, as seen in the diagram below:&#x20;

<figure><img src="../.gitbook/assets/All Templates + Notes (21).png" alt=""><figcaption></figcaption></figure>

In general, we recommend that the organization's highest-level governance surface wear the Top Hat; Workstreams, Teams, or Groups wear Level 1 hats (just below the Top Hat); and Individual Role Hats and Discrete Authority Hats (as described in the [What Hats Do I Need?](what-hats-do-i-need.md) page) are located at the lower-levels of the tree.

One exception to this guideline is if you want to establish a temporary Hats Admin Hat just beneath the Top Hat, to enable an individual EOA to set up and manage the Hats tree for a period of time before that Hats Admin Hat is later transferred or deactivated.
