---
description: How to Hat-gate Discord roles using Guild.xyz
---

# Guild.xyz --> Discord

## **Giving Hats Access to Specific Discord Roles and Channels with  Guild.xyz**

Following is a detailed description for how to use Guild.xyz to Hat-gate Discord roles and channels

#### **1. Connect your Discord server to Guild**

If you're new to Guild, [follow steps 1-5 found here](https://help.guild.xyz/en/articles/6947581-how-to-gate-a-discord-server).

If you already have a Guild set up, find your Guild, select "Add reward", and choose "Discord".

![](<../../../.gitbook/assets/Guild add reward.png>)![](<../../../.gitbook/assets/Guild rewards.png>)

Then, in your Discord server settings, add the Guild.xyz bot as an integration by navigating to the "Integrations" page under the "Apps" section. This will create a #verify channel in your Discord server where people can verify with Guild to gain access to the Discord roles associated with their Hat.

#### **2.Create a new role in Guild:**&#x20;

_If you already have a Guild role associated with this Hat, you can skip this step._

Navigate to your Guild and select "Add Role". We recommend creating a Guild role with the same name and image as the Hat you want to associated it with.

<figure><img src="../../../.gitbook/assets/Screenshot 2023-07-21 at 1.57.11 PM (1).png" alt=""><figcaption></figcaption></figure>

**3. Add a requirement that an address must hold a specific Hat token ID in order to claim that Guild role:**&#x20;

_If you have already associated that Guild role with the Hat token ID, you can skip this step._

Within that Guild role, select "Add Requirement"

<div align="left">

<figure><img src="../../../.gitbook/assets/Guild add requirement.png" alt="" width="375"><figcaption></figcaption></figure>

</div>

Then select "NFT"

![](<../../../.gitbook/assets/Guild select NFT.png>)



Next, input the chain your hat is on, add the Hats Protocol contract address, and enter the custom token ID associated with the hat. _See_ [#hats-protocol-contract-addresses-and-token-ids](../#hats-protocol-contract-addresses-and-token-ids "mention") _for details on how to find the Hats Protocol contract address and specific hat token IDs_.

![](<../../../.gitbook/assets/Guild add NFT requirement.png>)

Finally, select "Add requirement".&#x20;

This Guild role is now gated by the hat!

#### **4. Give that Guild role access to the Discord role you want to be associated with the hat:**

Within the Guild role, select "Add Reward", select "Add reward" within the Discord box, and connect the Guild role to a new Discord role or an already existing Discord role.&#x20;

<div align="left">

<figure><img src="../../../.gitbook/assets/Guilde add reward to role.png" alt="" width="375"><figcaption></figcaption></figure>

</div>

Save the Guild role. The hat now provides access to the designated Discord role via Guild!

#### 5. Give that Discord role access to specific permissions and channels within Discord

Open Discord and select the server associated with this role.&#x20;

From here, there are two means of setting the Discord authorities associated with this role.

First, open the Server Settings, and select Roles. From here you can manage the display, permissions, and other details of the Discord role associated with this hat.

<div align="left">

<figure><img src="../../../.gitbook/assets/Discord - edit role.png" alt="" width="375"><figcaption></figcaption></figure>

</div>

Second, select the specific Discord channels you want this role to have access to. Make sure these channels are set to "Private".&#x20;

Then, within each private channel you want to give this role access to, select "Add members or roles" and select the role associated with the hat.

![](<../../../.gitbook/assets/Discord edit channel.png>)![](<../../../.gitbook/assets/Discord add role to channel.png>)&#x20;

That's it, you're done! All hat wearers have to do to claim the Discord authorities associated with their hat is to visit the #verify channel in your Discord server.
