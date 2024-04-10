# 🧙 Admins: Creating, Issuing, and Revising Hats

## Overview

In Hats Protocol, admins are specific hats that can change a child hat's details, image, max supply, eligibility address, and toggle address — as long as that child hat is mutable (immutable hats cannot be changed once deployed). Admin hats can also mint both mutable and immutable hats to new wearers, and transfer mutable hats from one address to another.

Each hat is an admin of all other hats linked directly below it, as seen in the diagram below:&#x20;

<figure><img src="../../.gitbook/assets/All Templates + Notes (21).png" alt=""><figcaption></figcaption></figure>

Any Ethereum account can be a hat wearer: EOAs, DAOs, Smart Accounts (e.g. a Safe Multi-sig) or any other smart contract.&#x20;

## Autonomous Admins

As described above, any smart contract can also be a hat wearer. This enables organizations to use dedicated smart contracts in order to perform some Hats Admins operations in an automated manner, according to a predefined logic. These particular kind of hat wearers are called Autonomous Admins. One example is using an automated admin in order to automatically enable eligible accounts to [claim](../making-hats-claimable.md) certain roles instead of manually minting.

We typically recommend leaving space for an Autonomous Admin hat just below the Top Hat, from which the rest of the tree will emerge. At first this hat can be unworn, but as it is not yet possible to introduce new levels into your tree later without recreating your hats, creating this dedicated role will future-proof your tree for handling automation/operational needs. See the example below for our recommended placement of the Autonomous Admin hat.

<figure><img src="../../.gitbook/assets/Screenshot 2024-04-10 at 9.40.13 AM.png" alt=""><figcaption><p>TreasureDAO Hats tree for the Arbitrum Representative Council (ARC), featuring an Autonomous Admin hat: https://app.hatsprotocol.xyz/trees/42161/6</p></figcaption></figure>

Check out [this](../what-hats-do-i-need.md) guide for an overview of the different kinds of roles that a Hats Tree might include, and some general recommendations on how to structure them.
