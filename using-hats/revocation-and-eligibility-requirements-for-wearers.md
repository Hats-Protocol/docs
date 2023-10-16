# 🌟 Revocation & Eligibility: Requirements for Wearers

A hat’s eligibility module is an address that determines which addresses are eligible to wear that hat, and can revoke the hat if the wearer is no longer eligible. Eligibility modules can be humanistic (as in an EOA or multisig) or mechanistic (as in a contract with custom logic) to automatically and instantly revoke the hat based on pre-defined triggers.

<figure><img src="../.gitbook/assets/Screenshot 2023-06-28 at 3.15.24 PM.png" alt="" width="300"><figcaption></figcaption></figure>

## **Eligibility Criteria Examples**

You can currently automate the granting and revocation of roles and permissions based on:

* Token and NFT holdings (ERC20, ERC721, ERC1155)
* Active subscriptions
* Election results with term limits
* Reputation scores
* Contributions
* Staking to receive a role
* Allowlists
* Seasonality
* Specific roles or other hats

Coming soon:

* Onchain signature of an agreement
* Attestations
* Combine multiple criteria!
* Request a new module [here](https://hatsprotocol.deform.cc/getintouch/) or [create your own!](https://docs.hatsprotocol.xyz/for-developers/hats-modules) (see more details below in the “For Builders” section)

## How to Set the Eligibility for a given Hat

* Select "Edit Tree"
* Locate and select the hat
* Open the "Revocation & Eligibility" section

<figure><img src="../.gitbook/assets/Revocation And Eligibility.png" alt=""><figcaption></figcaption></figure>

You can choose between two types of modules:

#### Humanistic: EOA, Multisig Address, or DAO Contract Address&#x20;

* Choose "Manually" in order to set a humanistic type of eligibility (e.g. EAO or a Multisig)&#x20;
* Enter the address that will determine manually eligibility for that hat
* Optionally, add any relevant context by adding requirements as pairs of labels and external links

#### Mechanistic: Hats Modules

* Choose "Automatically" in order to set a mechanistic type of eligibility (e.g. ownership of a token), enabling the automatic granting and revocation of hats (and their associated permissions) based on specific conditions&#x20;

<figure><img src="../.gitbook/assets/Create Module (1).png" alt=""><figcaption></figcaption></figure>

## Hats Modules: Programmable Extensions for Roles & Permissions

Hats Modules are programmable extensions for roles. Modules can be connected to hats to expand their functionality, such as enabling automatic granting and revocation of hats (and their associated permissions) based on specific conditions. For more details on Hats Modules, including what they can unlock and how builders can create new modules, [see this blog post](https://hats.mirror.xyz/xAk\_yb7dDL1OLBx8nq47Ni7V1SuiC6L6B-49u7vz520).

To deploy an eligibility module for a given hat, first open the "Revocation and Eligibility" panel for a hat within Edit Mode and select "Automatically" as detailed above. Then:

* Choose "Create new Module"

<figure><img src="../.gitbook/assets/Create New Module.png" alt=""><figcaption></figcaption></figure>

* Choose one of the available modules ([see module descriptions here](https://docs.hatsprotocol.xyz/hats-integrations/eligibility-modules)). As an example, we'll use the ERC20 Eligibility module below, which defines eligibility by ownership of a minimum balance of a chosen amount of an ERC20 token

<figure><img src="../.gitbook/assets/ERC20 Eligibility.png" alt=""><figcaption></figcaption></figure>

* Choose the module-specific parameters
* Choose "Deploy & Return" to deploy the module and return to the hat edit form.&#x20;

You'll be able to continue making any edits to the hat(s) and deploy them once ready.

Go [here](../hats-integrations/eligibility-modules/) to check the complete list of available Eligibility modules, including a step-by-step creation guide for each. Additionally, it includes a guide on how to make hats claimable by eligible wearers.

## Unsure of Where to Start?

If you're not sure what a particular hat's eligibility or toggle modules should be at this point, consider: "who or what should this role be accountable to?"

For instance, it could make good sense to set the eligibility and toggle modules for a "Product Workstream Facilitator Hat" to the Product Workstream's multisig address. And, it could make sense to set the eligibility and toggle modules for the Product Workstream Hat to the organization's contract address.

For any hats you're still not sure about, we recommend setting their eligibility and toggle modules to the organization's contract address, at least to start. If the hats in question are mutable, their admins can always change their eligibility and toggle modules later.

## Digging Deeper

For more technical details on how Hats eligibility modules work, see the [Eligibility Modules](../for-developers/hats-protocol-overview/eligibility-modules.md) page within the "For Developers" section of these docs.
