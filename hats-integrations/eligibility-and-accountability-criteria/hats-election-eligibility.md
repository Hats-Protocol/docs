# Hats Election Eligibility

## **Overview**

A Hats Protocol Eligibility Module which sets eligibility for a hat based on the results of an election for a given term (conducted elsewhere). Terms are defined as the timestamp after the term ends. This contract allows for the next term to be set while the current term has not yet ended, which allows for an election for the next term to be conducted while the current term is still active.

The module's code is open source and is available [here](https://github.com/Hats-Protocol/hats-elections-eligibility).

## **Adding the module to a hat**

* Go to the tree that includes the hat you wish to create the module for
* Select "Edit Tree"
* Locate and select the hat
* Open the "Revocation & Eligibility" section
* Choose "Hats Election Eligibility" in the module type

<figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

* Fill in the module-specific parameters
* Choose "Deploy & Return" to deploy the module and return to the hat edit form. The module address will be automatically updated on the hat's eligibility property in the form. Once you deploy these changes, the hat's eligibility will be updated.

## Viewing the hat's eligibility criteria

Once the module is attached to the hat, you can view the hat's updated eligibility criteria:

* Select the hat
* In the eligibility section, you can view:
  * The module's public actions
  * The module's general description
  * The module's live parameters
    * Admin Hat ID
    * Ballot Box Hat ID
    * Ending time of the current term
    * Ending time of the next term, if scheduled
  * Useful links
    * The module's source code on GitHub

<figure><img src="../../.gitbook/assets/Screenshot 2024-02-15 at 12.02.37.png" alt="" width="563"><figcaption></figcaption></figure>

## Module's roles

The module has two special roles, which are set at the module's creation. Each role is granted to a hat/s, providing its wearers certain authorities in the module:

* Admin - can set up new terms.
* Ballot Box - can submit the election's results.

### Admin&#x20;

To view or perform the Admin's authorities:

* Select the admin hat
* In the Authorities section, locate the Elections Admin authority card

<figure><img src="../../.gitbook/assets/Screenshot 2024-02-15 at 12.11.29.png" alt="" width="563"><figcaption></figcaption></figure>

### Ballot Box

To view or perform the Ballot Box's authorities:

* Select the admin hat
* In the Authorities section, locate the Elections Ballot Box authority card

<figure><img src="../../.gitbook/assets/Screenshot 2024-02-15 at 12.18.35.png" alt="" width="563"><figcaption></figcaption></figure>
