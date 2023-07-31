# Toggle Modules

Toggle contracts have authority to switch the `hat.active` status of a hat, such as from `active` to `inactive`. When a hat is inactive, it does not have any wearers (i.e., the balance of its previous wearers' is changed to 0).

Any address can serve as a hat's toggle. As with eligibility modules, Hats Protocol supports two categories of toggle modules:

1. **Mechanistic toggles** are logic contracts that implement the [`IHatsToggle` interface](../v1-protocol-spec/interfaces/ihatstoggle.sol.md), which enables the hats contract to _pull_ a hat's active status by calling `checkToggle` from within the `Hats.balanceOf` function. Mechanistic toggle enable instantaneous deactivation (or reactivation) based on pre-defined logic, such as timestamps ("this hat expires at the end of the year").
2. **Humanistic toggles** are either EOAs or governance contracts. To deactivate (or reactivate) a hat, humanistic toggles must _push_ updates to the Hats contract by calling `Hats.toggleHatStatus`.

Unlike admins — and like [eligibility modules](eligibility-modules.md), toggle modules are explicitly set as addresses, not Hats.

Toggle modules offer a large design space for developers to extend and customize organizational infrastructure. See [Building Hats Modules](../building-hats-modules/) for more information.
