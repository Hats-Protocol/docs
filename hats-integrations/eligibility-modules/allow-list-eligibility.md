# Allow-List Eligibility

## **Overview**

A Hats Protocol eligibility module that uses an allowlist to determine eligibility.

This module sets up a simple allowlist to determine eligibility for a hat. For a given account (i.e. potential hat wearer), the allowlist stores values for that account's eligibility and standing for the hat. The wearer(s) of the `OWNER_HAT` can add or remove accounts from the allowlist. The wearer(s) of the `ARBITRATOR_HAT` can set the standing of accounts.

The module's code is open source and is available [here](https://github.com/Hats-Protocol/allowlist-eligibility/tree/main).

## **Adding the module to a hat**

* Go to the tree that includes the hat you wish to create the module for
* Select "Edit Tree"
* Locate and select the hat
* Open the "Revocation & Eligibility" section

<figure><img src="../../.gitbook/assets/Revocation And Eligibility Zoom.png" alt=""><figcaption></figcaption></figure>

* Choose "Automatically" and then choose "Create new Module". This will open the module creation form
* Choose "Allowlist Eligibility" in the module type

<figure><img src="../../.gitbook/assets/Allowlist Eligibility Guide.png" alt=""><figcaption></figcaption></figure>

* Fill in the module-specific parameters
* Choose "Deploy & Return" to deploy the module and return to the hat edit form. The module address will be automatically updated on the hat's eligibility property in the form. Once you deploy these changes, the hat's eligibility will be updated.

## Viewing the hat's eligibility criteria

Once the module is attached to the hat, you can view the hat's updated eligibility criteria:

* Select the hat
* In the eligibility section, you can view:
  * The module's public actions
  * The module's general description
  * The module's live parameters
    * Owner Hat ID
    * Arbitrator Hat ID
  * Useful links
    * The module's source code on GitHub

<figure><img src="../../.gitbook/assets/Screenshot 2024-02-15 at 12.39.36.png" alt="" width="563"><figcaption></figcaption></figure>

## Module's roles

The module has two special roles, which are set at the module's creation. Each role is granted to a hat, providing its wearers certain authorities in the module:

* Owner - can add and remove accounts from the allowlist.
* Arbitrator - can set the standing status of accounts.

### Owner&#x20;

To view or perform the Owner's authorities:

* Select the owner hat
* In the Authorities section, locate the Allowlist Owner authority card

<figure><img src="../../.gitbook/assets/Screenshot 2024-02-15 at 12.44.32.png" alt="" width="563"><figcaption></figcaption></figure>

### Arbitrator&#x20;

To view or perform the Arbitrator's authorities:

* Select the arbitrator hat
* In the Authorities section, locate the Allowlist Arbitrator authority card

<figure><img src="../../.gitbook/assets/Screenshot 2024-02-15 at 12.46.03.png" alt="" width="563"><figcaption></figcaption></figure>
