---
description: Tying hat eligibility to specific ERC1155 NFT holdings
---

# ERC1155 Eligibility

## **Overview**

A Hats eligibility module that makes addresses eligible to wear a given hat only if they have a specified minimum balance for at least one of specific ERC1155 token(s), as identified by contract address and token ID(s). This eligibility module can be configurable to support both single-token criteria as well as multiple-token criteria, where the balance requirement is configurable for each token.

The module's code is open source and is available [here](https://github.com/pumpedlunch/HatsEligibilityModules/blob/master/src/MultiERC1155EligibilityModule.sol).

## **Using the ERC1155 Eligibility Module**

* Go to the tree that includes the hat you wish to create the module for
* Select "Edit Tree"
* Locate and select the hat
* Open the "Revocation & Eligibility" section

<figure><img src="../../.gitbook/assets/Revocation And Eligibility Zoom.png" alt=""><figcaption></figcaption></figure>

* Choose "Automatically" and then choose "Create new Module". This will open the module creation form
* Choose "ERC1155 Eligibility" in the module type

<figure><img src="../../.gitbook/assets/ERC1155 Eligibility Guide.png" alt=""><figcaption></figcaption></figure>

* Fill in the module-specific parameters
* Choose "Deploy & Return" to deploy the module and return to the hat edit form
