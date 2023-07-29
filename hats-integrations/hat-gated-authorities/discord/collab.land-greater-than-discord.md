---
description: How to hat-gate Discord roles and channels with Collab.Land
---

# Collab.Land --> Discord

## **Giving Hats Access to Specific Discord Roles and Channels with  Collab.Land**

Following is a detailed description for how to use Collab.Land to hat-gate Discord roles and channels:

#### 1. Connect your Discord server to Collab.Land

Follow the [instructions found here](https://collab-land.gitbook.io/collab-land/bots/discord).

#### 2. Add a requirement that an address must hold a specific Hats token ID in order to claim a given Discord role

To create a Discord role associated with a specific hat, first navigate to your Discord server's settings. Then:

* Select "Roles"
* Select "Create Role"
* Create a new Discord role associated with a specific hat. We recommend using the same name and image as the hat, as seen in the [Hats app](https://app.hatsprotocol.xyz).

Then, back in Collab.Land:

* Navigate to the Token Granted Roles ("TGRs") page associated with your Discord server within Collab.Land
* Select "Select Role"
* Select the Discord role associated with this hat&#x20;

<figure><img src="../../../.gitbook/assets/collabland - tgrs discord.png" alt=""><figcaption></figcaption></figure>

You will then be asked to provide TGRs (token-gating requirements) for this role. Enter the following information:

* Enter the chain your Hats tree is on
* Select the "ERC1155" token type
* Add the Hats Protocol contract address
* Enter the custom token ID associated with the hat you are associating with this Discord role
* Choose a minimum balance of 1

_See_ [#hats-protocol-contract-addresses-and-token-ids](../#hats-protocol-contract-addresses-and-token-ids "mention") _for details on how to find the Hats Protocol contract address and specific hat token IDs_.

![](<../../../.gitbook/assets/Collabland add role requirements.png>)

#### 3. Give that Discord role access to specific permissions and channels within Discord

Open Discord and select the server associated with this role.&#x20;

From here, there are two means of setting the Discord authorities associated with this role.

First, open the Server Settings, and select Roles. From here you can manage the display, permissions, and other details of the Discord role associated with this hat.

<div align="left">

<figure><img src="../../../.gitbook/assets/Discord - edit role.png" alt="" width="375"><figcaption></figcaption></figure>

</div>

Second, select the specific Discord channels you want this role to have access to. Make sure these channels are set to "Private".&#x20;

Then, within each private channel you want to give this role access to, select "Add members or roles" and select the role associated with the hat.

![](<../../../.gitbook/assets/Discord edit channel.png>)![](<../../../.gitbook/assets/Discord add role to channel.png>)&#x20;

That's it, you're done! All Hat wearers have to do to claim the Discord authorities associated with their hat is to visit the #collabland-join channel that is now available in your Discord server, and connect their wallet using the Collab.Land bot.
