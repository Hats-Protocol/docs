---
description: How to give every hat a wallet
---

# Hats Wallet

Hats Wallet introduces role-based rewards, tying streamed rewards and compensation with a given role rather than specific addresses.&#x20;

<figure><img src="../../.gitbook/assets/hats wallet.jpg" alt=""><figcaption></figcaption></figure>

## Overview

One of the biggest challenges for DAOs today is the lack of accountability for paid contributors. It is an easy trap for a DAO to fall into, where contributor compensation is set up via DAO proposal, and some contributors are receiving large or recurring grants, but after some time, stop delivering work that is commensurate with that compensation. Right now, DAOs don't have a good way of holding those contributors accountable to following through on their responsibilities, and stopping compensation when appropriate.

For Hats Wallet we implemented a Hats-specific version of Mech from Gnosis Guild to give every hat its own smart contract wallet. Hats Wallets are wallets that are controlled by the DAO but can be delegated to specific individuals and tied to specific accountabilities.

**This unlocks three key capabilities:**

1. Hats Wallets give the DAO control over specific wallets as opposed to relying on individuals personal EOAs. This improves security.
2. Hats Wallets introduce role-based rewards, tying streamed rewards and compensation with a given role rather than specific addresses. This ensures good stewardship of the DAOs resources, and enables a more programmable and permissionless contribution-based reward structure.
3. Hats Wallets connect rewards and signing authority associated with a wallet to specific accountabilities. For example, if a facilitator role comes with control of a given Hats Wallet, and a specific requirement for keeping that roles is maintaining at least a 75% approval rating from their colleagues, the moment they fall below that threshold they will lose access to the rewards and authorities associated with that Hats Wallet.&#x20;

## **Using Hats Wallet**

_This integration is currently in beta. Contact us at support \[at] hatsprotocol \[dot] xyz if you want to explore this integration, or_ [_check out the Hats Wallet Github repo here_](https://github.com/Hats-Protocol/hats-wallet)_._
