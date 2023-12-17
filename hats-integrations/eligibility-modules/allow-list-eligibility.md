# Allow-List Eligibility

## **Overview**

A Hats Protocol eligibility module that uses an allowlist to determine eligibility.

This module sets up a simple allowlist to determine eligibility for a hat. For a given account (i.e. potential hat wearer), the allowlist stores values for that account's eligibility and standing for the hat. The wearer(s) of the `OWNER_HAT` can add or remove accounts from the allowlist. The wearer(s) of the `ARBITRATOR_HAT` can set the standing of accounts.

This module serves as both a "mechanistic" and "humanistic passthrough" eligibility module.

#### Mechanistic Functionality

* Wearer(s) of the `OWNER_HAT` can simply add account(s) to the allowlist by calling `addAccount()` or `addAccounts()`.
* Wearer(s) of the `OWNER_HAT` can simply remove account(s) from the allowlist by calling `removeAccount()` or `removeAccounts()`.
* Wearer(s) of the `ARBITRATOR_HAT` can simply set the standing of account(s) by calling `setStandingForAccount()` or `setStandingForAccounts()`.

In each of these cases, Hats Protocol will _pull_ eligibility and standing data from the module via `getWearerStatus()`. Hats Protocol will not emit an event with any of these eligibility and resulting wearer changes, so front ends pointing only at Hats Protocol events (or the subgraph) will not automatically reflect these changes.

#### Humanistic Functionality

* Wearer(s) of the `OWNER_HAT` can manually revoke an account's hat by calling `removeAccountAndBurnHat()`.
* Wearer(s) of the `ARBITRATOR_HAT` can manually put an account in bad standing and burn their hat by calling `setStandingForAccountAndBurnHat()`.

In these cases, the module _pushes_ eligibility and standing data to Hats Protocol, causing Hats Protocol to emit event(s) reflecting the eligibility and resulting wearer changes. Front ends pointing at Hats Protocol events (or the subgraph) _will_ automatically reflect these changes.

The module's code is open source and is available [here](https://github.com/Hats-Protocol/allowlist-eligibility/tree/main).

## **Using the** Allow-List **Eligibility Module**

* Go to the tree that includes the hat you wish to create the module for
* Select "Edit Tree"
* Locate and select the hat
* Open the "Revocation & Eligibility" section

<figure><img src="../../.gitbook/assets/Revocation And Eligibility Zoom.png" alt=""><figcaption></figcaption></figure>

* Choose "Automatically" and then choose "Create new Module". This will open the module creation form
* Choose "Allowlist Eligibility" in the module type

<figure><img src="../../.gitbook/assets/Allowlist Eligibility Guide.png" alt=""><figcaption></figcaption></figure>

* Fill in the module-specific parameters
* Choose "Deploy & Return" to deploy the module and return to the hat edit form
