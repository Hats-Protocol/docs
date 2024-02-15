# Hat-Wearing Eligibility

## **Overview**

A Hats Protocol eligibility module that conditions eligibility for one hat based on wearing another hat.

One use of a hat is to serve as an encapsulation of a set of logic and conditions that serve as baseline eligibility criteria for other hats. This eligibility module builds on that idea by allowing a hat to be used as an eligibility criterion for another hat.

The module's code is open source and is available [here](https://github.com/Hats-Protocol/hat-wearing-eligibility/tree/main).&#x20;

## **Adding the module to a hat**

* Go to the tree that includes the hat you wish to create the module for
* Select "Edit Tree"
* Locate and select the hat
* Open the "Revocation & Eligibility" section

<figure><img src="../../.gitbook/assets/Revocation And Eligibility Zoom.png" alt=""><figcaption></figcaption></figure>

* Choose "Automatically" and then choose "Create new Module". This will open the module creation form
* Choose "Hat Wearing Eligibility" in the module type

<figure><img src="../../.gitbook/assets/Hat Wearing Eligibility.png" alt=""><figcaption></figcaption></figure>

* Fill in the module-specific parameters
* Choose "Deploy & Return" to deploy the module and return to the hat edit form. The module address will be automatically updated on the hat's eligibility property in the form. Once you deploy these changes, the hat's eligibility will be updated.

## Viewing the hat's eligibility criteria

Once the module is attached to the hat, you can view the hat's updated eligibility criteria:

* Select the hat
* In the eligibility section, you can view:
  * The module's general description
  * The hat that it is required to be a wearer of for eligibility&#x20;
  * A link to the the module's source code on GitHub

<figure><img src="../../.gitbook/assets/Screenshot 2024-02-15 at 11.54.09.png" alt=""><figcaption></figcaption></figure>
