# Agreement Eligibility

## Overview

The agreement eligibility module requires someone to sign an agreement as a condition for claiming a given hat. This can be used for legal contracts, commitments of responsibility, or codes of conduct.&#x20;

When an individual signs the agreement, they also receive a hat that grants them access to the community. If a new agreement is published, community members must sign the new agreement in order to keep wearing the hat.

Adding an agreement module to a hat automatically creates a unique claim page for that hat, where users can view the agreement, sign it, claim the hat, and access the hat’s powers (like admission to a Discord server or multisig signing authority) all from a dedicated UI.&#x20;

<figure><img src="https://lh7-us.googleusercontent.com/4Q_N8zTAYZ5LB8zSpVdUNZQz9ZrmnP2jErMtpdQL6pmrZkyOR6u1rxXXsvghzgTL7Ao1rm5ORstOYVVnbn2hq29A4_jXX8jBI_-3M3zsfJKnqKRszDa-SX4rA3dmJYb8rY9T-iEtWPO_tBKC0SEE4ug" alt=""><figcaption><p>Claim-with-agreement page for the <a href="https://claim.hatsprotocol.xyz/10/78.1.5">All In For Sport Community Member hat</a></p></figcaption></figure>

**Case Study:** Hats protoDAO has automated the onboarding of over 200 community members into its communication channels and workspaces via the Hats Community Member hat, with minimal operational oversight. To claim the Community Member hat, individuals have to first sign a transaction confirming they agree to the Hats Community Agreements and Code of Conduct. Once claimed, the Community Member hat gives wearers access to the Community Telegram group, Charmverse workspace, and provides them with voting power in Snapshot and JokeRace. [See the full case study here.](https://www.hatsprotocol.xyz/wearer/hats-protodao)

## **Adding the module to a hat**

* Go to the tree that includes the hat you wish to create the module for
* Select "Edit Tree"
* Locate and select the hat
* Open the "Revocation & Eligibility" section
* Choose "Agreement Eligibility" in the module type

<figure><img src="../../.gitbook/assets/Screenshot 2024-02-20 at 9.05.24.png" alt="" width="563"><figcaption></figcaption></figure>

* Fill in the module-specific parameters
* Choose "Deploy & Return" to deploy the module and return to the hat edit form. The module address will be automatically updated on the hat's eligibility property in the form. Once you deploy these changes, the hat's eligibility will be updated.

## Viewing the hat's eligibility criteria

Once the module is attached to the hat, you can view the hat's updated eligibility criteria:

* Select the hat
* In the eligibility section, you can view:
  * The module's public actions
  * The module's general description
  * The module's live parameters
    * Current agreement
    * Grace period ending (relevant when the agreement was updated)
  * Useful links
    * The module's source code on GitHub

<figure><img src="../../.gitbook/assets/Screenshot 2024-02-20 at 10.27.38.png" alt="" width="563"><figcaption></figcaption></figure>
