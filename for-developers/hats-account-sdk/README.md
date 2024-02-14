# 💼 Hats Account SDK

## Overview

HatsAccount gives every Hats Protocol hat a smart contract account. Each hat can have multiple flavors of HatsAccount, each following the ERC6551 standard and designed to be deployed via the ERC6551Registry factory.

HatsAccount gives every hat the ability to do the following:

* Send ETH, ERC20, ERC721, and ERC1155 tokens
* Sign ERC1271-compatible messages, e.g. as a signer on a multisig
* Become a member of a DAO and make/vote on proposals, e.g. in a Moloch DAO
* Call functions on other contracts
* `Delegatecall` to other contracts, via [tokenbound](https://github.com/tokenbound/contracts)'s [sandbox](https://github.com/jaydenwindle/delegatecall-sandbox/) concept
* Be assigned permissions in address-based onchain access control schemes

Apart from the first and last, all of these actions are performed by the hat's wearer(s), with the security model determined by the flavor of HatsAccount.

The SDK is an open source JavaScript client for creating and interacting with Hats Account instances and was designed to work both in the browser and in Node.js.

{% content-ref url="1-of-n-hats-account/" %}
[1-of-n-hats-account](1-of-n-hats-account/)
{% endcontent-ref %}
