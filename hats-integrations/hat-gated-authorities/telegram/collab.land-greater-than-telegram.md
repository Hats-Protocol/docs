---
description: How to hat-gate Telegram channel access with Collab.Land
---

# Collab.Land --> Telegram

## **Giving Hats Access to Telegram via Collab.Land**

#### 1. Connect your Telegram channel to Collab.Land

[Follow steps 1-3 found here.](https://collabland.freshdesk.com/support/solutions/articles/70000637073-telegram-bot-walkthrough)

#### 2. Add a requirement that an address must hold a specific hat token ID in order to access the Telegram channel

Once you get to Step 4 [in the instruction link above](https://collabland.freshdesk.com/support/solutions/articles/70000637073-telegram-bot-walkthrough) to add Token Gating Access to your Telegram Channel via Collab.Land, add a TGA with the following details:

* Enter the chain your Hats are on
* Select the "ERC1155" token type
* Add the Hats Protocol contract address
* Enter the custom token ID associated with the hat
* Choose a minimum balance of 1

_See_ [#hats-protocol-contract-addresses-and-token-ids](../#hats-protocol-contract-addresses-and-token-ids "mention") _for details on how to find the Hats Protocol contract address and specific hat token IDs_.

![](<../../../.gitbook/assets/collabland TGA telegram.png>)

#### 3. Use the Collab.Land invite link for your Telegram Channel moving forward

In the "Bot Config / Invite Link", copy the invite link found there and use this to link to add hat wearers to the Telegram channel (the invite link provided directly by Telegram will no longer work).

That's it, you're done! All hat wearers have to do to access the Telegram channels associated with their hat is to visit the invite link you provide them and connect their wallet to the Collab.Land bot that will appear.
