# ⚡ Deactivating & Reactivating Hats

The [permissions and authorities](../../hats-integrations/permissions-and-authorities/) that can be accessed via a hat can be granted and revoked by designated individual or group admins, as well as based on a wide range of automated eligibility and accountability criteria using Hats Modules.&#x20;

[Hats Modules](https://hats.mirror.xyz/xAk\_yb7dDL1OLBx8nq47Ni7V1SuiC6L6B-49u7vz520) are programmable extensions for roles. Modules can be connected to hats to expand their functionality, such as enabling automatic granting and revocation of hats (and their associated permissions) based on specific conditions.&#x20;

A hat’s toggle module is an address that determines whether the hat is active or inactive for all wearers. Toggle modules can be humanistic (as in an EOA or multisig) or mechanistic (as in a contract with custom logic) to automatically and instantly deactivate/activate the hat based on pre-defined triggers.

<figure><img src="../../.gitbook/assets/Screenshot 2023-06-28 at 3.13.01 PM.png" alt="" width="563"><figcaption></figcaption></figure>

## **Toggle Examples**

Toggle triggers you may use to determine whether or not a hat is active include:

* **Seasonal or time-specific toggle** that automatically deactivates a hat at the end of a given season or period of time
* **Hat-based toggle** that enables the wearer/s of one hat to decide on the activation/reactivation of another.
* **Circuit-breaker toggle** to safeguard the DAO's assets and deactivate a set of hats and their associated authorities if certain conditions are met
* Any custom logic you can imagine that can be represented onchain

## How to Set the Toggle for a given Hat

* Select "Edit Tree"
* Locate and select the hat
* Open the "Deactivation & Reactivation" section

<figure><img src="../../.gitbook/assets/Deactivation And Reactivation.png" alt=""><figcaption></figcaption></figure>

You can choose between two types of modules:

#### Humanistic: EOA, Multisig Address, or DAO Contract Address

* Choose "Manually" in order to set a humanistic type of toggle (e.g. EAO or a Multisig)&#x20;
* Enter the address of the hat's toggle
* Optionally, add any relevant context by adding requirements as pairs of labels and external links

#### Mechanistic: Hats Modules

* Choose "Automatically" in order to set a mechanistic type of toggle (e.g. time-based automatic deactivation/activation)&#x20;

<figure><img src="../../.gitbook/assets/Create Toggle Module.png" alt=""><figcaption></figcaption></figure>

## Hats Modules: Programmable Extensions for Roles & Permissions

Hats Modules are programmable extensions for roles. Modules can be connected to hats to expand their functionality, such as enabling automatic deactivation and reactivation of hats (and their associated permissions) based on specific conditions. For more details on Hats Modules, including what they can unlock and how builders can create new modules, [see this blog post](https://hats.mirror.xyz/xAk\_yb7dDL1OLBx8nq47Ni7V1SuiC6L6B-49u7vz520).

To deploy a toggle module for a given hat, first open the "Deactivation & Reactivation" panel for a hat within Edit Mode and select "Automatically" as detailed above. Then:

* Choose "Create new Module"

<figure><img src="../../.gitbook/assets/Create Module 2.png" alt=""><figcaption></figcaption></figure>

* Choose one of the available modules. As an example, we'll use the Pass-through Toggle module which enables the wearers of one hat to decide on the deactivation/reactivation of another hat.

<figure><img src="../../.gitbook/assets/Hat-Based Toggle.png" alt=""><figcaption></figcaption></figure>

* Choose the module-specific parameters
* Choose "Deploy & Return" to deploy the module and return to the hat edit form.&#x20;

You'll be able to continue making any edits to the hat(s) and deploy them once ready.

Go [here](../../hats-integrations/activation-and-deactivation-criteria/) to check the complete list of available Toggle modules, including a step-by-step creation guide for each.&#x20;

## Digging Deeper

For more technical details on how Hats toggle modules work, see the [Toggle Modules](../../for-developers/hats-protocol-overview/toggle-modules.md) page within the "For Developers" section of these docs.
