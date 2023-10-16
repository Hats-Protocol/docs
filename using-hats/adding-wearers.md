# 🥳 Adding Wearers

Hats tokens can be held by any address including an EOA, multisig, or contract. When an address has a balance of 1 of a given Hats token, it is considered a "wearer" of that "hat". Then, by way of various token-gates, that address is granted the [authorities](connecting-hats-with-authorities/) that have been associated with that hat.

Each hat can have any number of wearers up to the hat’s max wearers. Hats are granted and revoked by the organization, or agents/smart contracts that are designated by the org. Wearers can renounce a hat, but they cannot transfer it.

### How to add new wearers for a given hat

* Select "Edit Tree"
* Locate and select the hat
* Open the "Wearers" section

<figure><img src="../.gitbook/assets/Add Wearers.png" alt=""><figcaption></figcaption></figure>

Then, add an address or ENS that is controlled by the intended wearer _(note: ensure the address is on the same chain as your Hats tree)_.

To add multiple wearers with one transaction, enter multiple addresses/ENS or upload a .csv containing a list of wearer addresses.

Once the changes are deployed, all the wearers of that hat will be shown in the sidebar under "Hat Wearers".

<figure><img src="../.gitbook/assets/Existing Wearers (2).png" alt=""><figcaption></figcaption></figure>

Once wearers are added, they can view the hats they're wearing by selecting "My Hats", see the associated responsibilities and authorities they hold, renounce a hat they are wearing, create new child hats underneath hats they are wearing, and make changes to any mutable hats they are an admin of.

### Max Wearers

The maximum number of addresses that can wear a given hat at once. Max wearers could be set to 1 to ensure only one address is holding that role at a given time, or it could be set as high as 4.29 billion (2^32).&#x20;
