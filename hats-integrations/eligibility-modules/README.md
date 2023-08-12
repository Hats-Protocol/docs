---
description: Requirements for Wearers
---

# 🌟 Eligibility Modules

A hat’s eligibility module is an address that determines which addresses are eligible to wear that hat, and can revoke the hat if the wearer is no longer eligible. Eligibility modules can be humanistic (as in an EOA or multisig) or mechanistic (as in a contract with custom logic) to automatically and instantly revoke the hat based on pre-defined triggers.

Eligibility modules can also be combined with [claimable hats](../claiming-and-onboarding-integrations/making-hats-claimable.md) to enable addresses to claim and wear a given hat _only if_ they fulfill specific eligibility criteria.

<figure><img src="../../.gitbook/assets/Screenshot 2023-06-28 at 3.15.24 PM.png" alt="" width="300"><figcaption></figcaption></figure>

## **Eligibility Criteria Examples**

Eligibility criteria you may use to determine which addresses are and are not eligible to wear a given hat include:

* **Assets** such as tokens, badges, and/or POAPs held by a given wallet address
* **Staking** requirements that specify an address must stake a minimum amount of a given token
* **Active subscription**, verifying whether or not an address is paying an ongoing fee (e.g., using Unlock Protocol)
* **Election results** specifying only the top N vote-getters of an election are eligible to wear a designated hat
* **Delegated tokens or votes** that reach and/or stay above a given threshold
* **Contributions and attestations** such as those represented by Govrn contributions, Quests NFTs, or EAS attestations
* **Humanistic eligibility** based on specified criteria (e.g., an arbitration council or stewardship council rules on hat eligibility according to predetermined rules)
* Any custom logic you can imagine that can be represented onchain

## Unsure of Where to Start?

If you're not sure what a particular hat's eligibility or toggle modules should be at this point, consider: "who or what should this role be accountable to?"

For instance, it makes good sense to set the eligibility and toggle modules for the Product Workstream Facilitator Hat to the Product Workstream's multisig address. And, it makes sense to set the eligibility and toggle modules for the Product Workstream Hat to the organization's contract address.

For any hats you're still not sure about, we recommend setting their eligibility and toggle modules to the organization's contract address, at least to start. If the hats in question are mutable, their admins can always change their eligibility and toggle modules later.

## Guides

See the subpages within this section for detailed guides for specific eligibility modules you can use with Hats:

{% content-ref url="erc20-eligibility.md" %}
[erc20-eligibility.md](erc20-eligibility.md)
{% endcontent-ref %}

{% content-ref url="jokerace-eligibility.md" %}
[jokerace-eligibility.md](jokerace-eligibility.md)
{% endcontent-ref %}

{% content-ref url="erc1155-eligibility.md" %}
[erc1155-eligibility.md](erc1155-eligibility.md)
{% endcontent-ref %}

{% content-ref url="staking-eligibility.md" %}
[staking-eligibility.md](staking-eligibility.md)
{% endcontent-ref %}

## Digging Deeper

For more technical details on how Hats eligibility modules work, see the [Eligibility Modules](../../for-developers/hats-protocol-overview/eligibility-modules.md) page within the "For Developers" section of these docs.
