# Gitcoin Passport Eligibility

## Overview

A Hats Protocol eligibility module for Gitcoin Passport that sets a target hat's eligibility based on a given Passport score criterion.

Note that Passport scores are stored offchain by default. In order to bring a score onchain, its owner can use Passport's [user interface](https://passport.gitcoin.co/#/dashboard):

<figure><img src="../../.gitbook/assets/Screenshot 2024-07-25 at 17.24.52.png" alt=""><figcaption></figcaption></figure>

Additionally, a score is currently valid for 90 days, and thus require an update by its owner in order to not lose eligibility.

The module's code is open source and is available [here](https://github.com/daocoa/gitcoin-passport-eligibility/tree/main).

## **Adding the module to a hat** <a href="#adding-the-module-to-a-hat" id="adding-the-module-to-a-hat"></a>

* Go to the tree that includes the hat you wish to create the module for
* Select "Edit Tree"
* Locate and select the hat
* Open the "Revocation & Eligibility" section

<figure><img src="../../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

* Choose "Automatically" and then choose "Create new Module". This will open the module creation form
* Choose "Gitcoin Passport Eligibility" in the module type

<figure><img src="../../.gitbook/assets/Screenshot 2024-07-25 at 18.36.33.png" alt=""><figcaption></figcaption></figure>

* Fill in the module-specific parameters
* Choose "Deploy & Return" to deploy the module and return to the hat edit form. The module address will be automatically updated on the hat's eligibility property in the form. Once you deploy these changes, the hat's eligibility will be updated.
