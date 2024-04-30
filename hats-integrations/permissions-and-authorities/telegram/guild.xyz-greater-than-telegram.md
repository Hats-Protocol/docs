---
description: How to hat-gate Telegram channel access with Guild.xyz
---

# Guild.xyz --> Telegram

**Giving Hats Access to Telegram via Guild.xyz**

#### **1. Connect your Telegram channel to Guild**

If you're new to Guild, [follow steps 1-7 found here](https://help.guild.xyz/en/articles/6947585-how-to-gate-a-telegram-group).

If you already have a Guild set up, find your Guild, select "Add reward", and choose "Telegram". Then [follow steps 4-7 found here](https://help.guild.xyz/en/articles/6947585-how-to-gate-a-telegram-group).

![](<../../../.gitbook/assets/Guild add reward.png>)![](<../../../.gitbook/assets/Guild rewards.png>)

#### **2.Create a new role in Guild:**&#x20;

_If you already have a Guild role associated with this hat, you can skip this step._

Navigate to your Guild and select "Add Role". We recommend creating a Guild role with the same name and image as the hat you want to associated it with.

<figure><img src="../../../.gitbook/assets/Screenshot 2023-07-21 at 1.57.11 PM.png" alt=""><figcaption></figcaption></figure>

#### **3. Add a requirement that an address must hold a specific hat token ID in order to claim that Guild role:**&#x20;

_If you have already associated that Guild role with the hat's token ID, you can skip this step._&#x20;

Otherwise, within that Guild role, select "Add Requirement"

<div align="left">

<figure><img src="../../../.gitbook/assets/Guild add requirement.png" alt="" width="375"><figcaption></figcaption></figure>

</div>

Then select "NFT"

![](<../../../.gitbook/assets/Guild select NFT.png>)



Next, input the chain your hats are on, add the Hats Protocol contract address, select "Custom ID" under Requirement type, and enter the custom token ID associated with the hat. _See_ [#hats-protocol-contract-addresses-and-token-ids](../#hats-protocol-contract-addresses-and-token-ids "mention") _for details on how to find the Hats Protocol contract address and specific hat token IDs_.

![](<../../../.gitbook/assets/Guild add NFT requirement.png>)

Finally, select "Add requirement".&#x20;

This Guild role is now gated by the hat!

#### **4. Give that Guild role access to the Telegram channel you want to be associated with the hat:**

Within the Guild role, select "Add Reward", select "Add reward" within the Telegram box, and connect the Guild role to the Telegram channel by adding the Guild bot to your Telegram channel and following the instructions to enter the Telegram group ID provided by the bot.&#x20;

<div align="left">

<figure><img src="../../../.gitbook/assets/Guilde add reward to role.png" alt="" width="375"><figcaption></figcaption></figure>

</div>

Save the Guild role. The hat now provides access to the designated Telegram channel via Guild!

_NOTE: Each Guild role can only grant access to one Telegram Channel. If you want to give a hat access to multiple Telegram channels, you will have to create multiple Guild roles associated with that hat._

That's it, you're done! All hat wearers have to do to claim the authorities associated with their hat is to visit your Guild page and claim the applicable Guild role(s).

## Link your Hats tree to Guild to automatically display Guild authorities

This step will enable the Hats app to automatically detect and display Guild.xyz related authorities in your Hats tree:

{% hint style="info" %}
Skip this step if your tree's top-hat already includes the relevant Guild(s).
{% endhint %}

* Select "Edit Tree"
* Locate and select the tree's top-hat
* In the "Hat Basics" section, add the relevant Guilds. A Guild's name can be found in its URL. For example, if the Guild page is https://guild.xyz/hats-protocol, then its name is 'hats-protocol'.

<figure><img src="../../../.gitbook/assets/Screenshot 2024-04-10 at 11.09.17.png" alt=""><figcaption></figcaption></figure>

Guild.xyz authorities will now be displayed on the relevant hats:

<figure><img src="../../../.gitbook/assets/Screenshot 2024-04-10 at 11.58.09.png" alt="" width="563"><figcaption></figcaption></figure>
