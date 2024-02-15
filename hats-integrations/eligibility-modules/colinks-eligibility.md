# CoLinks Eligibility

## **Overview**

A Hats Protocol Eligibility Module which determines eligibility based on the supply of CoLinks links targeting a given account. An account (i.e. potential hat wearer) is eligible if the current supply of their links meets a configurable threshold.

The module's code is open source and is available [here](https://github.com/Hats-Protocol/colinks-eligibility).

{% hint style="info" %}
Note: The [CoLinks](https://optimistic.etherscan.io/address/0x7154cA7E4C756E06151aefA2D765404950FA0EE1#code) contract is currently available on Optimism, and thus the module creation is available only on the Optimism network.
{% endhint %}

## **Adding the module to a hat**

* Go to the tree that includes the hat you wish to create the module for
* Select "Edit Tree"
* Locate and select the hat
* Open the "Revocation & Eligibility" section
* Choose "CoLinks Supply Eligibility" in the module type

<figure><img src="../../.gitbook/assets/Screenshot 2024-01-28 at 19.53.07.png" alt="" width="563"><figcaption></figcaption></figure>

* Fill in the module-specific parameters
* Choose "Deploy & Return" to deploy the module and return to the hat edit form. The module address will be automatically updated on the hat's eligibility property in the form. Once you deploy these changes, the hat's eligibility will be updated.

## Viewing the hat's eligibility criteria

Once the module is attached to the hat, you can view the hat's updated eligibility criteria:

* Select the hat
* In the eligibility section, you can view:
  * The module's general description
  * The module's live parameters
    * Link supply threshold
    * CoLinks contract address
  * Useful links
    * The module's source code on GitHub
    * CoLink's interface

<figure><img src="../../.gitbook/assets/Screenshot 2024-02-15 at 16.58.13.png" alt="" width="563"><figcaption></figcaption></figure>
