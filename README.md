---
description: >-
  Save time, automate onboarding, and make better decisions with programmable
  onchain roles
---

# 👋 Welcome to Hats Protocol

## Organizations work better with Hats

Hats turns organizations into a digital object, ready to be programmed. All of the properties of your organization and its individual roles and permissions can now be automated, just like any other software system.

At Hats Protocol, we are building public infrastructure for the next era of humanity. Here's an overview of what Hats is and how it works.

#### **Quick links:**

* [Website](https://hatsprotocol.xyz/)
* [Use cases & case studies](https://www.hatsprotocol.xyz/case-studies)
* [App](https://app.hatsprotocol.xyz/)
* [Foundational vision post](https://blog.hatsprotocol.xyz/organizational-graphs)
* [Blog](https://blog.hatsprotocol.xyz/)
* [Join the Hats Community & protoDAO](https://community.hatsprotocol.xyz/)

## What is Hats?

Hats is a full-stack solution for organizing onchain. Create your roles onchain to streamline permission management and introduce real accountability for your contributors.

[**Roles**](using-hats/what-hats-do-i-need.md) — which we call “hats” — are rich objects that conform to the ERC-1155 standard and that bundle responsibilities, permissions, and incentives. They are represented as tokens, which are held by [**agents**](using-hats/adding-wearers.md) (Ethereum accounts). Because of the flexibility of accounts in the EVM, they can easily be controlled by individuals, groups, DAOs, smart accounts, or AI agents, with any decision-making structure you can think of onchain.

<figure><img src="https://lh7-us.googleusercontent.com/XmvualHMUh27UvgJ3EVo2aHeag1aSn4tkmyZdmJ2q3iQjr-Ic_VsfGrIdWIJShTAVH6n9b41nMA9GSg5PK6uJJnIzVB53opG1tnClXK5mCxLCMtRdRCmEMDRyno2nUP9l_crFbKwCV6Ckk2oE0wWRxk" alt=""><figcaption></figcaption></figure>

The connections between the nodes of an organizational structure are the admin and accountability relationships between roles. [**Admins**](using-hats/setting-accountabilities/admins-creating-issuing-and-revising-hats.md) get certain in-protocol permissions, like being able to create new roles, select which agents will get each role, and modify the permissions delegated to a role so the agent can accomplish its responsibilities.

[**Accountability relationships**](using-hats/setting-accountabilities/eligibility-requirements-for-wearers.md) make it possible for any agent in the organization to hold the responsibility for evaluating and aligning another agent’s performance. They can revoke hats that are misused or no longer needed.&#x20;

In Hats Protocol, all of these interfaces are extensible by developers. Organizations can easily automate the granting and revoking of roles, admin relationships, and accountability using any criteria or logic. Hats ecosystem developers have already created over 15 automations that organizations can plug into their graphs without writing any code.

Of course, it is the [**permissions**](hats-integrations/permissions-and-authorities/) delegated to a hat that make it powerful. Specifically, we’ve seen that there are a few categories of permissions that are particularly important for organizational operations:

* Control of funds, operational budgets, and compensations streams&#x20;
* Ownership or voting power in domain-specific decisions
* Access to data, communication channels, and workspaces
* Ability to modify, publish, and execute code
* Identity that you can use to represent the organization in other contexts

<figure><img src="https://lh7-us.googleusercontent.com/4mAlQnmGQpwf4tN2s4lUvHZxP3FhYL0IY2F_9c6xsCQA3zq-aQWGWEO7UUAxtr_YZSeK4R8_XY0JAlWhQZvuJx7zVdo1ygRCtIim9HB0ThUdhLivIKPA-TT59MG8LnQWJoPuUVZE-nYQNSLMfjvCSvU" alt=""><figcaption><p>RareDAO is bringing its organizational graph onchain to create committees with accountability increase the efficiency of council transitions. <a href="https://www.hatsprotocol.xyz/case-studies">See this and other case studies here.</a></p></figcaption></figure>

Organizational efficiency is a function of pushing both decision-making and execution as close to the edges of the organization as possible. Hats enables this for onchain organizations, making it possible to get things done even with a widely distributed set of owners and stakeholders.

## How Does Hats Work?

Hats are programmable, revocable, and legible roles, which can be collectively controlled by the wearer of the "Top Hat", which could be an individual or a group, such as an organization. Hat-based roles can be flexibly imbued with responsibilities, authorities, accountabilities, context, and more.

Hats are represented onchain by tokens that conform to the ERC-1155 standard. They are connected together in a tree structure (aka a "Hats tree") to create flexible organizational structures that are controlled by an organization or its designees, which can then be visualized in any Hats front-end.

Hats tokens can be held by any address including an EOA, multisig, or contract. When an address has a balance of 1 of a given Hats token, it is considered a "wearer" of that "hat". Then, by way of various integrations and token-gates, that address is granted the [authorities](using-hats/connecting-hats-w-permissions-and-authorities/) that have been associated with that hat.

Each hat can have any number of wearers up to the hat’s max supply. Hats are granted and revoked by the organization, or agents/smart contracts that are designated by the org. Wearers can renounce a hat, but they cannot transfer it.

## Create Your Organizational Structure with Hats Protocol

The [Using the Hats App](broken-reference) section of these docs is devoted to documentation for Hats usage and setup by hat wearers, governance facilitators, and operations managers.&#x20;

In these pages, we emphasize the usage of the first front-end built by Haberdasher Labs for this purpose, but recognize that there will be many apps that are able to interact with Hats Protocol in our open-source ecosystem.

{% content-ref url="getting-started-with-hats.md" %}
[getting-started-with-hats.md](getting-started-with-hats.md)
{% endcontent-ref %}

## Developer Documentation

If you're a developer looking for more technical documentation, including contract functions, SDK details, subgraph information, and integration help, please jump directly to the [For Developers](broken-reference) section of these docs:

{% content-ref url="for-developers/hats-protocol-for-developers/" %}
[hats-protocol-for-developers](for-developers/hats-protocol-for-developers/)
{% endcontent-ref %}
