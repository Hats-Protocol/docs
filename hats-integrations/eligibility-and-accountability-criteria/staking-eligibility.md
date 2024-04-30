---
description: Tying hat eligibility to staking criteria
---

# Staking Eligibility

## **Overview**

The staking eligibility module requires an account to stake a minimum amount of tokens (like ETH, reputation points, or DAO tokens) in order to hold a given role and access its associated powers. If that address un-stakes their tokens, or their stake is slashed by a designated judge, their hat is automatically revoked.

Requiring staking for role eligibility enhances accountability for designated powers and provides a method for delegating responsibilities that cannot be enforced through code, such as social agreements. Staking eligibility also opens up the possibility for work to be more pseudonymous and less trustful: if you do the work well, you get compensated. If you do the work poorly, your stake can be slashed.

The module's code is open source and is available [here](https://github.com/Hats-Protocol/staking-eligibility).

Staking eligibility is one of the new modules we are most excited about, as the design space is enormous. If you’re keen to use it in your organization, [get in touch](https://hatsprotocol.deform.cc/getintouch/) and we can help you set it up!

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

<figure><img src="../../.gitbook/assets/image (1) (1).png" alt="" width="563"><figcaption></figcaption></figure>

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
