---
description: How to give specific hats voting access & voting weight in Snapshot polls
---

# Snapshot: Voting, Weight & Proposal Creation

## **The Basic Steps**

[Snapshot](https://www.snapshot.org) is an off-chain voting platform that allows communities to participate in the decentralized governance. But even though Snapshot votes happen off-chain, Snapshot can still read what hats an address is wearing to determine eligibility to create proposals, vote on proposals, and/or assign a specific voting weight.

#### There are three primary ways to attach Snapshot authorities to Hats:

1. Only allowing certain hats to create a new proposal
2. Only allowing certain hats to vote on a proposal
3. Assigning different voting weights to different hats

Following is a guide to implement each of these authorities.

* **Note: Distinct sets of strategies require distinct Snapshot spaces.** If you want to enforce different space settings for proposal creation, voting access, and voting weight (e.g., giving a specific hat voting access to vote on some proposals but not others), you will need to set up a different Snapshot space for each collection of settings. Fortunately, Snapshot makes it possible for organizations to create multiple spaces and link them together. [See here for more details on how to set up multiple spaces and link them together.](https://docs.snapshot.org/user-guides/spaces/sub-spaces)

### 1. Only allowing certain hats to make a new proposal

As an admin of your Snapshot space:

* Enter the Settings
* Select Proposal

Then under Validation, select Basic.&#x20;

<figure><img src="../../.gitbook/assets/Snapshot - proposals.png" alt=""><figcaption></figcaption></figure>

In the window that appears:

* Set "Minimum score" to 1
* Select "Use custom strategies"
* Select "erc1155-balance-of-ids" for the strategy
* Select the network your hats are on

![](<../../.gitbook/assets/Screenshot 2023-06-06 at 5.01.33 PM.png>)

Then enter the following under Params:

```json
{ 
"ids": [ "Hat-ID-1", "Hat-ID-2", "Hat-ID-3"],
 "address": "0x3bc1A0Ad72417f2d411118085256fC53CBdDd137" 
}
```

Replace Hat-ID-1, Hat-ID-2, and Hat-ID-3 with the specific hat token IDs that you want to give permission to post a new Snapshot proposal in this space (be sure to keep the quotations around each ID). You can add as many different hat token IDs as you want, using the convention above. _See_[#finding-a-hats-token-id](../../using-hats/connecting-hats-w-permissions-and-authorities/#finding-a-hats-token-id "mention") _for details on how to find specific hat token IDs._

### 2 & 3: Only allowing certain hats to vote on a proposal + assigning different voting weights to different hats

_These use cases are combined because they are implemented simultaneously._

As the admin of the Snapshot space:

* Enter the Settings
* Select Strategies

Here you can set up to 8 strategies for your Snapshot space. For the purposes of hat-gating voting access and voting weight, you will only need to set up one strategy (unless your hats are on different networks, in case you'll need one strategy per network).

<figure><img src="../../.gitbook/assets/Screenshot 2023-06-07 at 2.56.08 PM.png" alt=""><figcaption></figcaption></figure>

To set up a strategy:

* Click the "+ Add" button
* Select "erc1155-weighted-by-id" for the Strategy type
* Select the network your hats are on
* Enter the following into the box:

```json
{ 
"ids": ["Hat-ID-1", "Hat-ID-2"], 
"symbol": "Hats", 
"weight": [X, Y], 
"address": "0x3bc1A0Ad72417f2d411118085256fC53CBdDd137" 
}
```

Replace Hat-ID-1 and Hat-ID-2 with the specific hat token IDs that you want to give permission to vote on Snapshot proposals in this space (be sure to keep the quotations around each ID). You can add as many different Hat IDs as you want, using the convention above. _See_[#finding-a-hats-token-id](../../using-hats/connecting-hats-w-permissions-and-authorities/#finding-a-hats-token-id "mention") _for details on how to find specific hat token IDs._

And where X = the voting weight you want to assign to Hat-ID-1, Y = the voting weight for Hat-ID-3, and so on.&#x20;

**NOTE: Voting weight from Snapshot strategies is cumulative!** So if someone is wearing two different hats that are each allowed to vote on a proposal, one of which comes with a voting weight of 1 and the other with a voting weight of 2, they will actually be able to vote on the proposal with a voting weight of&#x20;

## Link your Hats tree to Snapshot to automatically display Snapshot authorities

This step will enable the Hats app to automatically detect and display Snapshot related authorities in your Hats tree:

{% hint style="info" %}
Skip this step if your tree's top-hat already includes the relevant Snapshot space(s).
{% endhint %}

* Select "Edit Tree"
* Locate and select the tree's top-hat
* In the "Hat Basics" section, add the relevant Snapshot spaces. A space ID can be found in its URL. For example, if the Snapshot space page is https://snapshot.org/#/hatsprotocol.eth, then its ID is 'hatsprotocol.eth'.

<figure><img src="../../.gitbook/assets/Add Snapshot Space.png" alt=""><figcaption></figcaption></figure>

Snapshot authorities will now be displayed on the relevant hats:

<figure><img src="../../.gitbook/assets/Snapshot Authority.png" alt=""><figcaption></figcaption></figure>
