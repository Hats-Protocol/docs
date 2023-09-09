---
description: Making hats claimable with a Claims Hatter contract
---

# Making Hats Claimable

## Overview

In Hats Protocol, hats are typically issued by admins minting them to wearers. While often that is the desired behavior, there are cases where it is desirable to allow wearers to claim a hat themselves, assuming they are eligible to wear them. ClaimsHatter is a [hatter contract](../../for-developers/hats-protocol-overview/hat-admins-and-hatter-contracts.md#hatter-contracts) that enables you to optionally make hats claimable by eligible wearers.

Making a hat claimable via ClaimsHatter involves the following steps:

1. Create a new instance of ClaimsHatter for the claimable hat
2. Mint or transfer an admin hat of the claimable hat to the ClaimsHatter instance from (1)
3. Set a [mechanistic eligibility module](../../for-developers/hats-protocol-overview/eligibility-modules.md) for the claimable hat
4. Eligible wearer(s) can now claim the hat

The guide below will walk you through the steps required to make a hat claimable.

## Prerequisites and setup

Making a hat claimable via ClaimsHatter includes a couple prerequisites.

First, the hat to claim must have an admin that can be worn by an instance of ClaimsHatter (see Step 2 below). In many cases, it is sufficient to mint any admin Hat to the instance of the ClaimsHatter contract you will create, even if that admin hat is worn by other wearers.&#x20;

However, in some cases, it will require creating an "extra" hat in between the hat to claim and what would otherwise be its admin hat.

For example, if in normal operations a hat tree would look like this...

```
   +-------------+
   | 1) Top Hat  |
   +-------------+
        |
   +---------------+
   | 1.1) Role Hat |
   +---------------+  
```

... then to make the Role Hat claimable, another hat needs to exist in between:

```
   +-------------+
   | 1) Top Hat  |
   +-------------+
        |
   +-----------------+
   | 1.1) Hatter Hat |
   +-----------------+
        |
   +---------------+
   | 1.2) Role Hat |
   +---------------+
```

Second, the hat to claim must have a [mechanistic eligibility module](../../for-developers/hats-protocol-overview/eligibility-modules.md), i.e. one that implements the [IHatsEligibility](https://github.com/Hats-Protocol/hats-protocol/blob/main/src/Interfaces/IHatsEligibility.sol) interface. Only such modules can create the "explicit eligibility" that ClaimsHatter requires.

## Claiming on behalf of a wearer

In some cases, it may be desirable to allow a third party — such as a bot network — to claim a hat on behalf of a wearer. Once enabled, anybody can then claim on behalf of an eligible wearer by calling the `claimFor` function.

## Step 1: Create a new instance of ClaimsHatter for the hat to claim

New instances of ClaimsHatter are deployed via the [HatsModuleFactory](https://github.com/Hats-Protocol/hats-module/blob/main/src/HatsModuleFactory.sol).

HatsModuleFactory is a clone factory that enables cheap creation of new module instances. The address of each instance is unique to the hat to claim (one ClaimsHatter per hat), and is deterministically generated.

To create a new instance of a ClaimsHatter contract for your soon-to-be-claimable hat, open the factory for the network your Hats are on. For example:

* [Goerli](https://goerli.etherscan.io/address/0x6D7E710BDbC80FC164ABA85e242E535c0A54CEc6#writeContract)
* [Optimism](https://optimistic.etherscan.io/address/0x6D7E710BDbC80FC164ABA85e242E535c0A54CEc6#writeContract)
* [Gnosis Chain](https://gnosisscan.io/address/0x6D7E710BDbC80FC164ABA85e242E535c0A54CEc6#writeContract)

Then, under "Contract" and "Write Contract":

* open the "createHatsModule" function
* in the `_implementation` input field, enter the ClaimsHatter implementation address: [0x11124220fe23Fd4d25C739508294E6b2305E073C](https://goerli.etherscan.io/address/0x11124220fe23fd4d25c739508294e6b2305e073c)
* in the `_hatId` input field, enter the token ID for the hat you want to make claimable _(see_ [#finding-a-hats-token-id](../../using-hats/connecting-hats-with-authorities/#finding-a-hats-token-id "mention") _for details on how to find specific hat token IDs)_
* in the `_otherImmutableArgs` input field just put the empty bytes string - `0x`.
* using the `_initData` input field, you can choose between the following options:
  *   To make the hat claimable on behalf of an eligible account, put:

      `0x0000000000000000000000000000000000000000000000000000000000000001`
  *   To make the hat claimable only by the eligible account itself, put:

      `0x0000000000000000000000000000000000000000000000000000000000000000`&#x20;
* write transaction

{% hint style="info" %}
Note that the "claimable for" functionality can be enabled/disabled by using the `enableClaimingFor`/`disableClaimingFor` functions. These functions can be called by an admin of the claimable hat.
{% endhint %}

Once the transaction has confirmed:&#x20;

* click "View your transaction"
* open "Logs"
* click the address to the right of instance (highlighted below), in the HatsModuleFactory\_ModuleDeployed event

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-07 at 16.08.20.png" alt=""><figcaption></figcaption></figure>

This is your new instance of the ClaimsHatter contract!

Next, within your new instance of the ClaimsHatter contract, you will need to:

* Select "Contract"
* Select "Is this a proxy?"
* Click "Verify" in the page that appears (as seen below)
* Click "Save"

<figure><img src="../../.gitbook/assets/Screenshot 2023-09-07 at 15.52.51.png" alt=""><figcaption></figcaption></figure>

You can now return to your instance of the ClaimsHatter contract, refresh the page, select "Contract" and select "Write as proxy".

Save this instance of the ClaimsHatter contract, as this is the contract that eligible wearers will use to claim their hat.

## Step 2: Mint or transfer an admin hat of the claimable hat to the ClaimsHatter instance

ClaimsHatter is a "hatter" contract, which is a type of contract designed to wear an admin hat. When wearing an admin hat (such as the "Hatter Hat" in the second diagram above), it gains admin authorities over the child hat(s) below it (such as the "Role Hat"). In ClaimsHatter's case, this includes the ability to mint those hat(s).

To enable ClaimsHatter to mint hats, it must be wearing an admin hat of the hat to claim. This can be done by minting (or transferring, as relevant) the admin hat to the address of the ClaimsHatter instance.

**Note: It is OK if the admin hat is also worn by other wearers in addition to the ClaimsHatter contract instance.**

## Step 3: Set a mechanistic eligibility module for the claimable hat

The hat to claim must have a [mechanistic eligibility module](../../for-developers/hats-protocol-overview/eligibility-modules.md), i.e. one that implements the [IHatsEligibility](https://github.com/Hats-Protocol/hats-protocol/blob/main/src/Interfaces/IHatsEligibility.sol) interface. Only such modules can create the "explicit eligibility" that ClaimsHatter requires.&#x20;

See the [Eligibility Modules](../eligibility-modules/) section of this guide for examples of possible mechanistic eligibility modules you could use.

If you explicitly want all addresses to be eligible to claim a given hat, you may use an AllEligible contract [such as this one](https://goerli.etherscan.io/address/0x4fb87569fcf9d31046193fd7a87b33e525a440c3) deployed on the Goerli testnet.&#x20;

## Step 4: Claiming

Once steps 1-3 have been completed, explicitly eligible wearers can now claim the claimable hat! They can do this simply by calling the `claim` function from the ClaimsHatter instance you created in Step 1.
