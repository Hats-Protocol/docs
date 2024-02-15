---
description: Tying hat eligibility to staking criteria
---

# Staking Eligibility

## **Overview**

Staking Eligibility is an eligibility module for Hats Protocol. It requires wearers of a given hat to stake a minimum amount of a specified token in order to be eligible, and enables others in the Hats tree's organization to slash the stake of a wearer who is behaving badly.

The module's code is open source and is available [here](https://github.com/Hats-Protocol/staking-eligibility).

## **Adding the module to a hat**

* Go to the tree that includes the hat you wish to create the module for
* Select "Edit Tree"
* Locate and select the hat
* Open the "Revocation & Eligibility" section

<figure><img src="../../.gitbook/assets/Revocation And Eligibility Zoom.png" alt=""><figcaption></figcaption></figure>

* Choose "Automatically" and then choose "Create new Module". This will open the module creation form
* Choose "Staking Eligibility" in the module type

<figure><img src="../../.gitbook/assets/Staking Eligibility Guide.png" alt=""><figcaption></figcaption></figure>

* Fill in the module-specific parameters
* Choose "Deploy & Return" to deploy the module and return to the hat edit form. The module address will be automatically updated on the hat's eligibility property in the form. Once you deploy these changes, the hat's eligibility will be updated.

## Viewing the hat's eligibility criteria

Once the module is attached to the hat, you can view the hat's updated eligibility criteria:

* Select the hat
* In the eligibility section, you can view:
  * The module's public actions
  * The module's general description
  * The module's live parameters
    * Staking token
    * Minimum required stake
    * Judge Hat ID (Can Slash Wearers)
    * Recipient Hat ID (Can Withdraw Slashed Stakes)
  * Useful links
    * The module's source code on GitHub

<figure><img src="../../.gitbook/assets/image (1).png" alt="" width="563"><figcaption></figcaption></figure>

## Module's roles

The module has two special roles, which are set at the module's creation. Each role is granted to a hat, providing its wearers certain authorities in the module:

* Judge - can slash wearers.
* Recipient - can withdraw slashed stakes.

### Judge&#x20;

To view or perform the Judge's authorities:

* Select the judge hat
* In the Authorities section, locate the Staking Judge authority card

<figure><img src="../../.gitbook/assets/Screenshot 2024-02-15 at 16.41.13.png" alt="" width="563"><figcaption></figcaption></figure>

### Recipient&#x20;

To view or perform the Recipient's authorities:

* Select the recipient hat
* In the Authorities section, locate the Staking Recipient authority card

<figure><img src="../../.gitbook/assets/Screenshot 2024-02-15 at 16.42.03.png" alt="" width="563"><figcaption></figcaption></figure>
