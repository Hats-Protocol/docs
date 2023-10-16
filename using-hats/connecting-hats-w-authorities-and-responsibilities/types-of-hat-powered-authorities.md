# Types of Hat-Powered Authorities

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
