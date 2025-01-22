---
description: How to hat-gate signing authority on a Safe multisig
---

# Safe Multisig Signing Authority

{% hint style="info" %}
This guide refers to v1 of Hats Signer Gate, which is being deprecated in favor of Hats Signer Gate v2. Existing instances of HSG v1 will continue to be supported. This note will be removed once these docs have been updated to reflect v2.
{% endhint %}

[Hats Signer Gate](https://github.com/Hats-Protocol/hats-zodiac#hats-signer-gate) is a contract that grants Safe multisig signing rights to addresses wearing a given hat, enabling on-chain organizations (such as DAOs) to delegate revocable constrained signing authority and responsibility to individuals.

**Case Study:** Treasure is building the “decentralized game console” on Arbitrum to power next-gen gaming onchain. As a highly active participant in the Arbitrum ecosystem, TreasureDAO is the second largest delegate by voting power in the Arbitrum DAO. Hats, in partnership with Gnosis Guild, enables TreasureDAO to give more voice to its community through the formation of an Arbitrum Council (ARC) consisting of its community members. ARC members, called ARC Liaisons, are now able to represent TreasureDAO in Arbitrum governance and vote with the delegated $ARB in a safe and secure way. [See the full case study here.](https://www.hatsprotocol.xyz/wearer/treasure-case-study)

_NOTE: We take security seriously and our contracts_ [_have been audited_](../../for-developers/hats-security-audits.md)_. When used properly, Hats Signer Gate enables secure transfer of safe signing authority from one address to another. However, with improper configurations, Hats Signer Gate can behave differently than designed and could result in lost funds. If you are interested in using Hats Signer Gate, contact us at support \[at] hatsprotocol \[dot] xyz for implementation support. Otherwise, be sure to heed the_ [_conditions for safe use_](safe-multisig-signing-authority.md#conditions) _below and use at your own risk._

## Technical Overview of Hats Signer Gate

There are two components to the Hats Signer Gate contract:

### **Zodiac Module**

[HatsSignerGate.sol](https://github.com/Hats-Protocol/hats-zodiac/blob/main/src/HatsSignerGate.sol) is a **Zodiac module** that...

1. Grants multisig signing rights to addresses based on whether they are wearing the appropriate hat(s).
2. Removes signers who are no long valid (i.e. no longer wearing the signer hat)
3. Manages the multisig threshold within the [owner](https://github.com/Hats-Protocol/hats-zodiac#contract-ownership)-specified range as new signers are added or removed.

**NOTE:** For security reasons, you cannot use Hats Signer Gate with other Zodiac modules

### **Zodiac Guard**

Since hat-wearing is dynamic, as hats can be programmatically revoked from wearers, this contract also services as a **Zodiac guard** to ensure that:

A) **Only valid signers can execute transactions**, i.e. only signatures made by accounts currently wearing a valid signer hat count towards the threshold.

B) **Signers cannot execute transactions that remove the constraint in (A)**. Specifically, this contract guards against signers...

1. Removing the contract as a guard on the multisig
2. Removing the contract as a module on the multisig — or removing/changing/adding any other modules,
3. Changing the multisig threshold
4. Changing the multisig owners

> Warning: Protections against (3) and (4) above only hold if the Safe does not have any authority over the signer hat(s). If it does — e.g. it wears an admin hat of the signer hat(s) or is an eligibility or toggle module on the signer hat(s) — then in some cases the signers may be able to change the multisig threshold or owners.
>
> Proceed with caution if granting such authority to a Safe attached to HatsSignerGate.

For more details on Hats Signer Gate including security audit results, [see here](https://github.com/Hats-Protocol/hats-zodiac/blob/main/README.md).

## Using Hats Signer Gate

There are five steps required to properly implement Hats Signer Gate:

1. Create the hats that will have multisig signing authority and note their token IDs. _See_ [_Finding a Hat's Token ID_](../../using-hats/connecting-hats-w-permissions-and-authorities/connecting-hats-to-token-gates/finding-a-hats-token-id.md) _for details on how to find specific hat token IDs_.
2. Deploy a new Hats Signer Gate contract (deployed via the [Hats Signer Gate Factory](https://github.com/Hats-Protocol/hats-zodiac/releases/tag/v1.2-beta))
3. Set up the Hats Signer Gate Zodiac module
4. Set up the Hats Signer Gate Zodiac guard
5. Mint Hats to wearers and have them claim signing authority

**Note:** If you create a new Safe in the process of deploying Hats Signer Gate in Step 2a, you can skip Steps 3 and 4! Your Zodiac module and Zodiac guard will have been automatically added to a new Safe and ready to go.

### 1. Create the Hats that will have multisig signing authority

Before continuing onto subsequent steps, it is first necessary to create the hats that you want to A) have signing authority on the multisig, and B) be the owners of the Hats Signer Gate contract (see below). You will need to enter the token IDs for each of these hats when first deploying your instance of the Hats Signer Gate contract.

You can easily create new Hats using the [Hats app](https://app.hatsprotocol.xyz) (but you do not need to mint them to any wearers yet). For a detailed guide for creating new Hats, see the [Getting Started](../../for-developers/v1-sdk/core/getting-started.md) page within these docs.

Once the owner and signer Hats are created, note their hat token IDs. _See_ [#finding-a-hats-token-id](../../using-hats/connecting-hats-w-permissions-and-authorities/#finding-a-hats-token-id "mention") _for details on how to find specific hat token IDs_.

### 2a. Deploy a new Hats Signer Gate contract using the Hats Signer Gate Factory

In the Hats App, enter edit mode and select the Authorities section:

<figure><img src="../../.gitbook/assets/Screenshot 2024-10-13 at 22.48.53.png" alt="" width="563"><figcaption></figcaption></figure>

Select "Add a Safe":

<figure><img src="../../.gitbook/assets/Screenshot 2024-10-13 at 22.52.35.png" alt=""><figcaption></figcaption></figure>

**Note:** make sure that you're connected to the chain in which your Hats are on.

If you already have a multisig set up that you'd like to use, select either:

* **Deploy Hats Signer Gate:** for cases where only one distinct hat will be a signer on the multisig, or
* **Deploy Multi Hats Signer Gate:** to enable multiple distinct hats to be signers on the multisig

If you would like to set up a new multisig to use with Hats Signer Gate, select either:

* **Deploy Hats Signer Gate and Safe**, or
* **Deploy Multi Hats Signer Gate and Safe**

**Note worth repeating:** If you create a new Safe in the process of deploying Hats Signer Gate in Step 2a, you can skip Steps 3 and 4! Your Zodiac module and Zodiac guard will have been automatically added to a new Safe and ready to go.

Complete the deployment process:

<figure><img src="../../.gitbook/assets/Screenshot 2024-10-13 at 23.15.05.png" alt=""><figcaption></figcaption></figure>

Following are additional explanations regarding the HSGs parameters:

1. **Owner Hat ID:** The wearer of the Owner Hat can make the following changes to Hats Signer Gate:
   1. "Transfer" ownership to a new hat&#x20;
   2. Set the acceptable multisig threshold range by changing Min Threshold and Target Threshold
   3. Add other Zodiac modules to the multisig
   4. In Multi-Hats Signer Gate, add other hats as valid signer hats
2. **Signer Hat IDs:** The ID or multiple IDs of the hats that will have signing authority on the multisig.&#x20;
3. **Min Threshold:** The fewest number of signers that can execute a transaction, even as signers are getting added to the safe. A minimum threshold is necessary to set, as signers may claim their signing authority at different times.&#x20;
4. **Target Threshold:** Once enough signers get added to the multisig by claiming signing authority, they will reach the target threshold, at which point this becomes the fewest number of signers that can execute a transaction.

For example, with a min threshold of 2 and a target threshold of 3...

* The first signer (1/1) to claim signing authority cannot execute transactions
* Once the second signer claims signing authority, the safe will be a 2/2
* Once the third signer claims signing authority, the safe will be a 3/3
* With a fourth signer, the safe will have reached its target threshold and become a 3/4
* The safe will then be a 3/N safe up to N = max signers

5. **Max Signers:** The maximum number of addresses that can claim signing authority on the Safe.

Once deployed, you'll get links to the Safe and the new HSG or MHSG contract:

<figure><img src="../../.gitbook/assets/Screenshot 2024-10-13 at 23.30.21.png" alt="" width="375"><figcaption></figcaption></figure>

### 2b. Connect your new multisig to the Safe app

_NOTE: Step 2b is only necessary if you created a new Safe multisig in the previous transaction_.

To connect your new multisig to the Safe app:

* Visit [**app.safe.global**](https://app.safe.global)
* Select **Add Existing Account**
* **Enter a name** for your new multisig
* **Enter the Safe address** you saved above
* Click **Next**

The Safe owner you see listed on the following page is the new Hats Signer Gate contract you deployed. This signer will be replaced as soon as an authorized hat wearer claims signing authority for the first time.

_If you created a new Safe in the process of deploying Hats Signer Gate, you can skip Steps 3 and 4!_ Your Zodiac module and Zodiac guard have automatically been added to the new Safe and are ready to go. Proceed to Step 5.

### 3. Set up the Hats Signer Gate Zodiac module

**If you are using an existing Safe, continue through Steps 3 and 4:**

To set up the Hats Signer Gate Zodiac module for your Safe:

* Open your Safe multisig in a new tab
* Under **Apps**, select **Zodiac**

<figure><img src="../../.gitbook/assets/Screenshot 2023-06-07 at 5.35.56 PM.png" alt=""><figcaption></figcaption></figure>

* Select **Open Safe App**
* Select **Custom Module**
* In the **Module Address** field, enter the address of your new Hats Signer Gate contract that you saved above
* Select **Add Module**
* Submit your transaction

![](<../../.gitbook/assets/Screenshot 2023-06-07 at 5.37.50 PM.png>)![](<../../.gitbook/assets/Screenshot 2023-06-07 at 5.37.58 PM.png>)

### 4. Set up the Hats Signer Gate Zodiac guard

Adding the HatSignerGate guard to your Safe multisig is a very important step that cannot be overlooked _(unless you created a new Safe in the process of deploying Hats Signer Gate in Step 2a, in which case you can skip step 4 as your Zodiac guard will have been automatically added to your new Safe and is ready to go)_.&#x20;

To complete this step:&#x20;

* Within the Safe app, select "New transaction" and then "Contract interaction"

<figure><img src="../../.gitbook/assets/Screenshot 2023-06-12 at 5.51.11 PM.png" alt="" width="375"><figcaption></figcaption></figure>

* Enter the address of your Safe multisig in the address field
* Select "use implementation ABI"

<figure><img src="../../.gitbook/assets/Screenshot 2023-06-12 at 5.52.22 PM.png" alt="" width="375"><figcaption></figcaption></figure>

* From the Contract Method Selector dropdown, select "setGuard"
* Enter the address of the Signer Gate contract you created in Step 2
* Select "Add transaction"

<figure><img src="../../.gitbook/assets/Screenshot 2023-06-12 at 5.55.47 PM.png" alt="" width="375"><figcaption></figcaption></figure>

* Select "Create batch" and "Send batch"
* Sign and execute the transaction

### 5. Mint hats to wearers and have them claim signing authority

Nearly done! The final step is to mint the appropriate hats (corresponding to the hat token IDs you gave signing authority to) to the addresses you want to claim signing authority.&#x20;

Once these hats are minted, all wearers need to do to claim signing authority is to:&#x20;

* Select the hat
* In the Authorities section, locate the HSG Signer authority card

<figure><img src="../../.gitbook/assets/Screenshot 2024-10-13 at 23.36.23.png" alt="" width="563"><figcaption></figcaption></figure>

* Select "Claim signer rights"

## FAQs

#### **How do you revoke signing authority?**

At any point hereafter, as soon as an address has lost its mutisig signer hat, anyone can call the removeSigner function in the Hats Signer Gate contract you deployed above by entering the address that should be removed from the multisig and processing the transaction.

**Will signers be able to sign and execute transactions if they've lost their multisig signer hat but are still on the Safe?**

No — this is the function of the Guard. The moment an address is no longer wearing its multisig signer hat, it will immediately be unable to sign or execute transactions.

## Conditions for Safe Use of Hats Signer Gate <a href="#conditions" id="conditions"></a>

The following conditions apply to all versions of Hats Signer Gate and Multi Hats Signer Gate. These conditions must be met to safely use Hats Signer Gate and avoid accidental bricking of your safe.

**Context:** It is possible to accidentally brick the Hats Signer Gate-connected safe if your organization loses its ability to transfer the signer hats to new wearers. If that happens, and if too many signers ghost, then the remaining signers won't be able to reach the required signer threshold and funds would get stuck.

In this case, the safe is recoverable if the wearer of the Owner Hat is able to reduce the minimum threshold, or is able to set additional hats as signers in the case of Multi Hats Signer Gate. However, these contingencies require that the wearer of the Owner Hat is not also the safe.

Under certain conditions, it's also possible for the existing signers to accidentally or maliciously brick the safe. Specifically, if the safe is an admin of the signer hat(s), it is possible for the safe to do the following:

* Transfer away too many of its current signer hats, in the case where signer hats are mutable, resulting in a bricked safe.
* Maliciously changing or removing the eligibility or toggle modules and setting the signer hats to immutable to prevent other admins from changing the hats back. This would result in the existing signers having total control of the safe.
* In the case where signer hat(s) are immutable, if the safe serves as the eligibility module for the signer hat(s), then the safe could be bricked if there are enough signers that ghost.

**These mistakes are easily avoided using the following guidelines for the Owner Hat and signer hat(s):**

DOs

* DO ensure there is always a functional eligibility module (aka accountability address) for the signer hat(s) that is not controlled by the safe
* DO ensure there is always a functional toggle module (aka accountability address) for the signer hat(s) that is not controlled by the safe

DON'Ts

* DON'T have the safe wear a hat that is an admin of the Owner Hat
* DON'T have the safe wear a hat that is an admin of any mutable signer hat(s)
  * _If signer hats are in the admin path of the safe, they must have a functional eligibility module (aka accountability address) that is not controlled by the safe, AND the signer hats must be immutable such that the safe cannot use its admin powers to remove or change the eligibility and toggle modules for the signer hat(s)._
* DON'T set the safe as the eligibility module (aka accountability address) of the Owner Hat NOR the signer hat(s)
* DON'T set the safe as the toggle module (aka activation address) of the Owner Hat NOR the signer hat(s)
