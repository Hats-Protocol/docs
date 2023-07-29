# Wearing a Hat

The wearer of a given hat is assigned the authorities and responsibilities associated with the Hat.

A wearer's status relating to a given hat is determined by three factors. All three must be true.

1. Whether their address has a balance (of 1) of the Hat's token
2. Whether the Hat is active (see the Toggle section for more detail)
3. Whether they are eligible (see the Eligibility section for more detail)

All of these factors are reflected in the `Hats.balanceOf` function, which will return `0` if any of the factors are false.

Any address can wear a hat, including:

* Externally Owned Accounts (EOAs)
* Logic contracts (i.e., contracts with explicit logic codified within functions), or
* Governance contracts (e.g., DAOs, multisigs, etc.)
