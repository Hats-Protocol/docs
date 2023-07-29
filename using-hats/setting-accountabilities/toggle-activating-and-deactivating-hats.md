# ⚡ Toggle: Activating & Deactivating Hats

A hat’s toggle module is an address that determines whether the hat is active or inactive for all wearers, which can also be humanistic or mechanistic.

<figure><img src="../../.gitbook/assets/Screenshot 2023-06-28 at 3.13.01 PM.png" alt="" width="563"><figcaption></figcaption></figure>

## **Toggle Examples**

Toggle triggers you may use to determine whether or not a hat is active include:

* **Seasonal or time-specific toggle** that automatically deactivates a hat at the end of a given season or period of time
* **Circuit-breaker toggle** to safeguard the DAO's assets and deactivate a set of hats and their associated authorities if certain conditions are met
* Any custom logic you can imagine that can be represented onchain

## Unsure of Where to Start?

If you're not sure what a particular hat's eligibility or toggle modules should be at this point, consider: "who or what should this role be accountable to?"

For instance, it makes good sense to set the eligibility and toggle modules for the Product Workstream Facilitator Hat to the Product Workstream's multisig address. And, it makes sense to set the eligibility and toggle modules for the Product Workstream Hat to the organization's contract address.

For any hats you're still not sure about, we recommend setting their eligibility and toggle modules to the organization's contract address, at least to start. If the hats in question are mutable, their admins can always change their eligibility and toggle modules later.

## Digging Deeper

For more technical details on how Hats toggle modules work, see the [Toggle Modules](../../for-developers/hats-protocol-overview/toggle-modules.md) page within the "For Developers" section of these docs.
