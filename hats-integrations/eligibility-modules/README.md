---
description: Requirements for Wearers
---

# 🌟 Eligibility Modules

Hats Modules are programmable extensions for roles. Modules can be connected to hats to expand their functionality, such as enabling automatic granting and revocation of hats (and their associated permissions) based on specific conditions.&#x20;

A hat’s eligibility module is an address that determines which addresses are eligible to wear that hat, and can revoke the hat the instant the wearer is no longer eligible.

<figure><img src="../../.gitbook/assets/Screenshot 2023-06-28 at 3.15.24 PM.png" alt="" width="300"><figcaption></figcaption></figure>

For more details on Hats Modules, including what they can unlock and how builders can create new modules, [see this blog post](https://hats.mirror.xyz/xAk\_yb7dDL1OLBx8nq47Ni7V1SuiC6L6B-49u7vz520). You can also [visit this docs page](../../using-hats/setting-accountabilities/eligibility-requirements-for-wearers.md) for a general guide about Eligibility Modules.

See the subpages within this section for detailed guides for specific eligibility modules you can currently use with Hats:

{% content-ref url="erc20-eligibility.md" %}
[erc20-eligibility.md](erc20-eligibility.md)
{% endcontent-ref %}

{% content-ref url="erc721-eligibility.md" %}
[erc721-eligibility.md](erc721-eligibility.md)
{% endcontent-ref %}

{% content-ref url="erc1155-eligibility.md" %}
[erc1155-eligibility.md](erc1155-eligibility.md)
{% endcontent-ref %}

{% content-ref url="staking-eligibility.md" %}
[staking-eligibility.md](staking-eligibility.md)
{% endcontent-ref %}

{% content-ref url="jokerace-eligibility.md" %}
[jokerace-eligibility.md](jokerace-eligibility.md)
{% endcontent-ref %}

{% content-ref url="pass-through-hat-based-eligibility.md" %}
[pass-through-hat-based-eligibility.md](pass-through-hat-based-eligibility.md)
{% endcontent-ref %}

{% content-ref url="hat-wearing-eligibility.md" %}
[hat-wearing-eligibility.md](hat-wearing-eligibility.md)
{% endcontent-ref %}

{% content-ref url="allow-list-eligibility.md" %}
[allow-list-eligibility.md](allow-list-eligibility.md)
{% endcontent-ref %}

Eligibility modules can also be combined with claimable hats to enable addresses to claim and wear a given hat _only if_ they fulfill specific eligibility criteria. For more information, check out the guide [here](../claiming-and-onboarding-integrations/making-hats-claimable.md).

## **Modules Coming Soon**

* Onchain signature of an agreement
* Gitcoin Passport score
* Attestations
* Combine multiple criteria!
* Request a new module [here](https://hatsprotocol.deform.cc/getintouch/) or [create your own!](https://docs.hatsprotocol.xyz/for-developers/hats-modules)

## Digging Deeper

For more technical details on how Hats eligibility modules work, see the [Eligibility Modules](../../for-developers/hats-protocol-overview/eligibility-modules.md) page within the "For Developers" section of these docs.

## Building Modules

Modules customize, automate, and extend the behavior of Hats Protocol, and can also serve as adapters or integration points with other protocols and applications.

In a sense, modules are the lifeblood of Hats Protocol. The design space is wide open, ready to be filled with all the possible building blocks of human organization and coordination.

There are two primary ways for developers to work with Hats Modules. Whether you're [building new modules](../../for-developers/hats-modules/building-hats-modules/) or using the [Modules SDK](../../for-developers/hats-modules/modules-sdk/) to interact with or build applications for existing modules, we have a number of developer tools to make your job easier. See the page below to get started.

{% content-ref url="../../for-developers/hats-modules/" %}
[hats-modules](../../for-developers/hats-modules/)
{% endcontent-ref %}
