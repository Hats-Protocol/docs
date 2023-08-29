# 🔐 Connecting Hats With Authorities

## **Hats + Gates --> Authorities**

Hats are ERC-1155 tokens, so they can be plugged into token gates to grant the wearers of that hat specific authorities, as long as 1) the wearer’s address is still eligible to wear the hat, and 2) the hat is still active.

You can think of it this way: token gates have two parts, the token and the gate. Hats provides the token, which gets plugged into the necessary gates, to give the hat wearer access to the proper authorities.&#x20;

<figure><img src="../../.gitbook/assets/Group 167.png" alt=""><figcaption></figcaption></figure>

## Types of Hat-Powered Authorities

Authorities can include hard powers, such as explicit onchain or offchain permissions provided through token gates (see below), as well as soft powers provided through social agreements and other accountability mechanisms, such as the authority to facilitate a meeting, work on projects in a given domain, or hold admin rights for a specific app that can't yet be token-gated.

You'll attach these authorities to your hats via token-gates after your hats are created onchain.

Authorities can be linked to hats in a number of ways, including via:

* **Token-gating platforms** including [Guild](https://guild.xyz/), [Collab.Land](https://www.collab.land/), and [Lit Protocol](https://litprotocol.com/), which provide token-gating for the following apps:
  * [**Guild**](https://guild.xyz/guildverse)**:** [Coordinape](https://docs.coordinape.com/info/integrations/guild), [Discord](https://guild.xyz/brain/discord), [Github](https://guild.xyz/brain/github) (private repos only), [Google Workspace](https://guild.xyz/brain/google-workspace) (Docs, Sheets, Slides), [Party.Space](https://guild.xyz/brain/party.space), [POAP](https://guild.xyz/brain/poap),  [Rally](https://guild.xyz/brain/rally), [Telegram](https://guild.xyz/brain/telegram), and [Wonderverse](https://guild.xyz/brain/wonderverse)
  * [**Collab.Land:**](https://www.collab.land/) [Discord](https://collab-land.gitbook.io/collab-land/bots/discord) and [Telegram](https://collab-land.gitbook.io/collab-land/bots/telegram)
  * [**Lit Protocol**](https://litprotocol.com/)**:** [Gather Town](https://www.youtube.com/watch?v=kDpKhMUNuqE\&ab\_channel=CryptoArcade), [Google Drive](https://litgateway.com/apps/google-drive), [Headline](https://viaheadline.xyz/), [IPFS](https://litgateway.com/files), [Nowhere](https://www.urnowhere.com/), [Orbis Club](https://orbis.club/), [Shopify](https://apps.shopify.com/lit-token-access), [WalletChat](https://lit.walletchat.fun/), [Wordpress](https://litgateway.com/apps/wordpress), and [Zoom](https://litgateway.com/apps/zoom)
* **Apps that integrate token-gating** to provide access to specific channels and read/write permissions, including [Charmverse](https://www.charmverse.io/), [Wonderverse](https://www.wonderverse.xyz/), and (soon) [Commonwealth](https://commonwealth.im/)
* **Tools that read ERC1155s for modifying parameters**, such as using [Snapshot Strategies](https://snapshot.org/) to allow only certain hats to vote in Snapshot proposals and/or give certain hats greater voting weight in Snapshot proposals
* [**HatsSignerGate**](https://github.com/Hats-Protocol/hats-zodiac)**, a Zodiac module that provides Safe multisig signing authority for a given set of hats**
* **Social agreements or other accountability mechanisms**, including seasonal elections, staking requirements, and/or reputation systems. Authorities that can't be explicitly granted to a hat via token-gating can still be granted to a hat wearer by using the hat as a signal of social agreement that the wearer has that authority.

See the subpages within the [Hat-Gated Authorities](../../hats-integrations/hat-gated-authorities/) section for detailed guides for connecting specific authorities to hats:&#x20;

{% content-ref url="../../hats-integrations/hat-gated-authorities/" %}
[hat-gated-authorities](../../hats-integrations/hat-gated-authorities/)
{% endcontent-ref %}

## Connecting Authorities to Hats

Hats are the tokens that give wearers access to token-gated permissions. Plugging a hat's token ID into a token gate will give all wearers of that hat access to the specified credential, as long as the wearer remains eligible to wear that hat and the hat remains active.

To connect a hat to a token-gate, locate the token-gating permissions for the platform or application you wish to use. In many cases, the process requires that you create a specific role in the platform that has special permissions associated with that role, and then add a specific requirement necessary for a user to hold that role (e.g., holding a particular Hats token). _See the_ [_Hat-Gated Authorities_](../../hats-integrations/hat-gated-authorities/) _section of these docs for guides for connecting hats to specific authorities and platforms._

At Guild.xyz, for example, which provides token-gating for Discord, Telegram, Github, and Google Workspace, you will create a role within your Guild, provide that Guild role with specific "rewards" (aka permissions), and then add a requirement that an address must have possession of a particular NFT to hold that Guild role.

![](https://hackmd.io/\_uploads/BkTwIJXBn.png) ![](https://hackmd.io/\_uploads/By7qBkXHn.png)

To connect a hat to a token-gate, you will need to add an NFT (ERC1155) requirement. Then, you'll need to enter two details:

1. The Hats Protocol contract address, and
2. The Hats token ID (sometimes called a Custom ID) for the appropriate hat. This token ID will be the same for all wearers of a single hat.

See below for these details.

{% content-ref url="hats-protocol-contract-addresses.md" %}
[hats-protocol-contract-addresses.md](hats-protocol-contract-addresses.md)
{% endcontent-ref %}

{% content-ref url="finding-a-hats-token-id.md" %}
[finding-a-hats-token-id.md](finding-a-hats-token-id.md)
{% endcontent-ref %}
