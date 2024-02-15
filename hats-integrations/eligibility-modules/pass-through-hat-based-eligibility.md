# Pass-Through (Hat-Based) Eligibility

## **Overview**

A Hats Protocol module that enables an authorized hat to serve as the eligibility and/or toggle module for other hat(s).

In Hats Protocol v1, eligibility and toggle modules are set as addresses. This creates a lot of flexibility, since addresses can be EOAs, multisigs, DAOs, or even other smart contracts. But hats themselves cannot be set explicitly as eligibility or toggle modules because hats are identified by uint256 hat IDs, not addresses.

Passthrough Module is a contract that can be set as the eligibility and/or toggle module for a target hat, and allows the wearer(s) of another hat to call the eligibility and/or toggle functions of the target hat. This allows hats themselves to be used as eligibility and toggle modules.

This contract is a "humanistic" module, not a "mechanistic" module. It does not inherit from `IHatsEligibility.sol` or `IHatsToggle.sol`, so Hats Protocol cannot pull any data from it. It serves only as a passthrough, enabling the wearer(s) of the authorized hat to push eligibility and toggle data about the target hat to Hats Protocol.

The module's code is open source and is available [here](https://github.com/Hats-Protocol/passthrough-modules).

## **Adding the module to a hat**

* Go to the tree that includes the hat you wish to create the module for
* Select "Edit Tree"
* Locate and select the hat
* Open the "Revocation & Eligibility" section

<figure><img src="../../.gitbook/assets/Revocation And Eligibility Zoom.png" alt=""><figcaption></figcaption></figure>

* Choose "Automatically" and then choose "Create new Module". This will open the module creation form
* Choose "Passthrough Eligibility and/or Toggle" in the module type

<figure><img src="../../.gitbook/assets/Pass-through Eligibility Guide.png" alt=""><figcaption></figcaption></figure>

* Fill in the module-specific parameters
* Choose "Deploy & Return" to deploy the module and return to the hat edit form. The module address will be automatically updated on the hat's eligibility property in the form. Once you deploy these changes, the hat's eligibility will be updated.

## Viewing the hat's eligibility criteria

Once the module is attached to the hat, you can view the hat's updated eligibility criteria:

* Select the hat
* In the eligibility section, you can view:
  * The module's general description
  * The module's live parameters
    * Eligibility Hat ID
  * Useful links
    * The module's source code on GitHub

<figure><img src="../../.gitbook/assets/Screenshot 2024-02-15 at 16.45.38.png" alt="" width="563"><figcaption></figcaption></figure>

## Module's roles

The module has one special role, which is set at the module's creation. The role is granted to a hat, providing its wearers certain authorities in the module:

* Eligibility Hat - can set the hat's wearers eligibility status.

### Eligibility&#x20;

To view or perform the Eligibility's authorities:

* Select the eligibility hat
* In the Authorities section, locate the Eligibility/Toggle Passthrough authority card

<figure><img src="../../.gitbook/assets/Screenshot 2024-02-15 at 16.47.48.png" alt="" width="563"><figcaption></figcaption></figure>
