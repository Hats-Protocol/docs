---
description: Tying hat eligibility to specific ERC721 NFT holdings
---

# ERC721 Eligibility

## **Overview**

A Hats Protocol eligibility module that checks if an address owns a minimum balance of an ERC721 token to determine eligibility.

The module's code is open source and is available [here](https://github.com/pumpedlunch/HatsEligibilityModules/blob/master/src/ERC721EligibilityModule.sol).

## **Adding the module to a hat**

* Go to the tree that includes the hat you wish to create the module for
* Select "Edit Tree"
* Locate and select the hat
* Open the "Revocation & Eligibility" section

<figure><img src="../../.gitbook/assets/Revocation And Eligibility Zoom.png" alt=""><figcaption></figcaption></figure>

* Choose "Automatically" and then choose "Create new Module". This will open the module creation form
* Choose "ERC721 Eligibility" in the module type

<figure><img src="../../.gitbook/assets/ERC721 Eligibility Guide.png" alt=""><figcaption></figcaption></figure>

* Fill in the module-specific parameters
* Choose "Deploy & Return" to deploy the module and return to the hat edit form. The module address will be automatically updated on the hat's eligibility property in the form. Once you deploy these changes, the hat's eligibility will be updated.

## Viewing the hat's eligibility criteria

Once the module is attached to the hat, you can view the hat's updated eligibility criteria:

* Select the hat
*   In the eligibility section, you can view:

    * The module's general description
    * The module's live parameters
      * The ERC-721 token address
      * The minimum balance required for eligibility&#x20;
    * Useful links
      * The module's source code on GitHub

    <figure><img src="../../.gitbook/assets/image.png" alt="" width="563"><figcaption></figcaption></figure>
