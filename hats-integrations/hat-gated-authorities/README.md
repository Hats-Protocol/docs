---
description: Hats + Gates --> Authorities
---

# 🔐 Hat-Gated Authorities

Hats are ERC1155 tokens, so they can be plugged into token gates to grant the wearers of that hat specific authorities, as long as 1) the wearer’s address is still eligible to wear the hat, and 2) the hat is still active.

You can think of it this way: token gates have two parts, the token and the gate. Hats provides the token, which gets plugged into the necessary gates, to give the hat wearer access to the proper authorities.

<figure><img src="../../.gitbook/assets/Group 167 (2).png" alt=""><figcaption></figcaption></figure>

For general information on types of authorities and how to connect authorities to specific hats, see the guide for [Connecting Hats With Authorities](../../using-hats/connecting-hats-with-authorities/).

To connect a hat to a token-gate, you will need to add an NFT (ERC-1155) requirement. Then, you'll need to enter two details:

1. The Hats Protocol contract address for the chain you're using (see below), and
2. The Token ID (sometimes called a Custom ID) for the appropriate hat. This Token ID will be the same for all wearers of a single hat.

See below for these details.

## Hats Protocol Contract Addresses and Token IDs

To connect specific hats to token gates, you will need the Hats Protocol contract address as well as the specific token IDs for the relevant hats you want to associated with that token gate.&#x20;

### Hats Protocol contract address

Hats Protocol has the same contract address for each chain is it deployed to (ENS: v1.hatsprotocol.eth): `0x3bc1A0Ad72417f2d411118085256fC53CBdDd137`

See below for links to the specific contracts for each chain:

* [**Ethereum (mainnet)**](https://etherscan.io/address/0x3bc1A0Ad72417f2d411118085256fC53CBdDd137)
* [**Arbitrum**](https://arbiscan.io/address/0x3bc1A0Ad72417f2d411118085256fC53CBdDd137)
* [**Gnosis Chain**](https://gnosisscan.io/address/0x3bc1A0Ad72417f2d411118085256fC53CBdDd137)
* [**Optimism**](https://optimistic.etherscan.io/address/0x3bc1A0Ad72417f2d411118085256fC53CBdDd137)
* [**Polygon**](https://polygonscan.com/address/0x3bc1A0Ad72417f2d411118085256fC53CBdDd137)
* [**Goerli (testnet)**](https://goerli.etherscan.io/address/0x3bc1A0Ad72417f2d411118085256fC53CBdDd137)

### Finding a hat's Token ID

To find a hat's token ID, locate and select that hat in the [Hats app](https://app.hatsprotocol.xyz) and click the copy icon to the right of the hat's "pretty ID" (found in the green box below).&#x20;

<figure><img src="../../.gitbook/assets/hat ID.png" alt=""><figcaption></figcaption></figure>

In decimal format, the hat's token ID will look something like this: `2588155291428878043886873276096123268223378170452611674367766728540160`.

In hexadecimal format, the same hat's token ID will look something like this: `0x0000006000010001000200000000000000000000000000000000000000000000`.

The Hats app converts the hexadecimal version to the "pretty id" format `96.1.1.2`:

* `0x00000060` converts to `96`
* `0x0001` converts to `1`
* `0x0001` converts to `1`
* `0x0002` converts to `2`

_For more technical details on how the Hats addressable ID system works, see the_ [_Hat IDs_](../../for-developers/hats-protocol-overview/hat-ids.md) _page within the "For Developers" section of these docs._

## Guides

See the subpages within this section for detailed guides for connecting specific authorities to hats:

{% content-ref url="coordinape.md" %}
[coordinape.md](coordinape.md)
{% endcontent-ref %}

{% content-ref url="council-voting-vault.md" %}
[council-voting-vault.md](council-voting-vault.md)
{% endcontent-ref %}

{% content-ref url="charmverse.md" %}
[charmverse.md](charmverse.md)
{% endcontent-ref %}

{% content-ref url="discord/" %}
[discord](discord/)
{% endcontent-ref %}

{% content-ref url="google-workspace.md" %}
[google-workspace.md](google-workspace.md)
{% endcontent-ref %}

{% content-ref url="hats-wallet.md" %}
[hats-wallet.md](hats-wallet.md)
{% endcontent-ref %}

{% content-ref url="safe-multisig-signing-authority.md" %}
[safe-multisig-signing-authority.md](safe-multisig-signing-authority.md)
{% endcontent-ref %}

{% content-ref url="telegram/" %}
[telegram](telegram/)
{% endcontent-ref %}

{% content-ref url="snapshot-voting-weight-and-proposal-creation.md" %}
[snapshot-voting-weight-and-proposal-creation.md](snapshot-voting-weight-and-proposal-creation.md)
{% endcontent-ref %}

{% content-ref url="wonderverse.md" %}
[wonderverse.md](wonderverse.md)
{% endcontent-ref %}
