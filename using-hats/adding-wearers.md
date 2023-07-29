# 🥳 Adding Wearers

Hats tokens can be held by any address including an EOA, multisig, or contract. When an address has a balance of 1 of a given Hats token, it is considered a "wearer" of that "hat". Then, by way of various token-gates, that address is granted the [authorities](connecting-hats-with-authorities.md) that have been associated with that hat.

Each hat can have any number of wearers up to the hat’s max supply. Hats are granted and revoked by the organization, or agents/smart contracts that are designated by the org. Wearers can renounce a hat, but they cannot transfer it.

### How to add new wearers for a given hat

To add new wearers for a specific hat:

* Locate and select the hat in the [Hats app](https://app.hatsprotocol.xyz)
* Select "Add a wearer"

<figure><img src="../.gitbook/assets/Screenshot 2023-07-13 at 1.40.45 AM.png" alt=""><figcaption></figcaption></figure>

Then, add an address or ENS that is controlled by the intended wearer _(note: ensure the address is on the same chain as your Hats tree)_, and select "Mint Hat".

To add multiple wearers with one transaction, enter multiple addresses by using the checkmark to add additional addresses, or upload a .csv containing a list of wearer addresses.

All the wearers of that hat will be shown in the sidebar under "Hat Wearer"

Once wearers are added, they can use the [Hats app](https://app.hatsprotocol.xyz) to view the hats they're wearing by selecting "My Hats", see the associated responsibilities and authorities they hold, renounce a hat they are wearing, create new child hats underneath hats they are wearing, and make changes to any hats they are an admin of.
