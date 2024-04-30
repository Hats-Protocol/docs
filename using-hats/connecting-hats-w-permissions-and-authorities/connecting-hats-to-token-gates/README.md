# Connecting Hats to Token Gates

Hats are ERC1155 tokens, so they can be plugged into token gates to grant the wearers of that hat specific authorities, as long as 1) the wearer’s address is still eligible to wear the hat, and 2) the hat is still active.

You can think of it this way: token gates have two parts, the token and the gate. Hats provides the token, which gets plugged into the necessary gates, to give the hat wearer access to the proper authorities.

<figure><img src="../../../.gitbook/assets/Group 167.png.webp" alt=""><figcaption></figcaption></figure>

To connect a hat to a token-gate, locate the token-gating permissions for the platform or application you wish to use. In many cases, the process requires that you create a specific role in the platform that has special permissions associated with that role, and then add a specific requirement necessary for a user to hold that role (e.g., holding a particular Hats token). _See the_ [_Hat-Gated Authorities_](../../../hats-integrations/permissions-and-authorities/) _section of these docs for guides for connecting hats to specific authorities and platforms._

### Example - Guild.xyz

At Guild.xyz, for example, which provides token-gating for Discord, Telegram, Github, and Google Workspace, you will create a role within your Guild, provide that Guild role with specific "rewards" (aka permissions), and then add a requirement that an address must have possession of a particular NFT to hold that Guild role.

![](https://hackmd.io/\_uploads/BkTwIJXBn.png) ![](https://hackmd.io/\_uploads/By7qBkXHn.png)

To connect a hat to a token-gate, you will need to add an NFT (ERC1155) requirement. Then, you'll need to enter two details:

1. [The Hats Protocol contract address](hats-protocol-contract-addresses.md), and
2. [The Hats token ID](finding-a-hats-token-id.md) (sometimes called a Custom ID) for the appropriate hat. This token ID will be the same for all wearers of a single hat.

See below for these details.

{% content-ref url="hats-protocol-contract-addresses.md" %}
[hats-protocol-contract-addresses.md](hats-protocol-contract-addresses.md)
{% endcontent-ref %}

{% content-ref url="finding-a-hats-token-id.md" %}
[finding-a-hats-token-id.md](finding-a-hats-token-id.md)
{% endcontent-ref %}

Finally, associate your Hats tree with the Guild/s:

* Select "Edit Tree"
* Locate and select the tree's top-hat
* Select the "Hat Basics" section
* Set the Guild name/s in the "Guilds" field

<figure><img src="../../../.gitbook/assets/Top Hat Guilds And Snapshot (1).png" alt=""><figcaption></figcaption></figure>

Now, Guild authorities will be automatically displayed on the relevant hats.

<figure><img src="../../../.gitbook/assets/Guild Authorities.png" alt=""><figcaption></figcaption></figure>
