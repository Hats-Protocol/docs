---
description: A smart contract account for every hat.
---

# Hats Account

<figure><img src="../../.gitbook/assets/hats wallet.jpg" alt=""><figcaption></figcaption></figure>

## Overview

Hats Account gives every Hats Protocol hat a smart contract account, following the [ERC-6551](https://eips.ethereum.org/EIPS/eip-6551) standard. A Hats Account instance is only controlled by the current wearers of its hat.

By Using Hats Account, DAOs are able to delegate certain authorities to predefined roles rather than directly to individuals/groups. Then, individuals/groups that hold these roles can access these authorities, while staying accountable to the DAO.

A Hats Account can perform any operations that EOAs or other smart contract accounts can, for example:

* Send/receive ETH, ERC20, ERC721 and/or ERC1155 tokens
* Become a member of a DAO and make and/or vote on proposals, e.g. in a Moloch DAO
* Be assigned permissions in address-based onchain access control schemes, e.g. via [Zodiac](https://zodiac.wiki/index.php/Introduction:\_Zodiac\_Standard) or [OpenZeppelin](https://docs.openzeppelin.com/contracts/5.x/access-control) access control contracts.
* Call functions on any other contracts

## **Using Hats Account**

A Hats Account instance address is deterministically determined by the hat it is tied to. This fact allows using the account even before it was deployed, e.g. setting up permissions or sending tokens to it.&#x20;

To deploy the account:

1. Select the hat you want to deploy the account for
2. Select the Hats Account authority card

<figure><img src="../../.gitbook/assets/Screenshot 2024-03-21 at 12.46.21.png" alt="" width="563"><figcaption></figcaption></figure>

3. Select "Deploy" in order to create the Hats Account instance, or "Got to HatsWallet" in order to view its address on a blockchain explorer.&#x20;
