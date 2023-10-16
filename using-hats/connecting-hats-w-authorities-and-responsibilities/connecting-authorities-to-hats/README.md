# Connecting Authorities to Hats

Hats are the tokens that give wearers access to token-gated permissions. Plugging a hat's token ID into a token gate will give all wearers of that hat access to the specified credential, as long as the wearer remains eligible to wear that hat and the hat remains active.

To connect a hat to a token-gate, locate the token-gating permissions for the platform or application you wish to use. In many cases, the process requires that you create a specific role in the platform that has special permissions associated with that role, and then add a specific requirement necessary for a user to hold that role (e.g., holding a particular Hats token). _See the_ [_Hat-Gated Authorities_](../../../hats-integrations/hat-gated-authorities/) _section of these docs for guides for connecting hats to specific authorities and platforms._

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
