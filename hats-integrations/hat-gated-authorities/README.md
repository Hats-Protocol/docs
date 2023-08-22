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

{% content-ref url="../../using-hats/connecting-hats-with-authorities/hats-protocol-contract-addresses.md" %}
[hats-protocol-contract-addresses.md](../../using-hats/connecting-hats-with-authorities/hats-protocol-contract-addresses.md)
{% endcontent-ref %}

{% content-ref url="../../using-hats/connecting-hats-with-authorities/finding-a-hats-token-id.md" %}
[finding-a-hats-token-id.md](../../using-hats/connecting-hats-with-authorities/finding-a-hats-token-id.md)
{% endcontent-ref %}

## Guides for Connecting Authorities to Hats

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

{% content-ref url="hats-signer-gate-safe-multisig-signing-authority.md" %}
[hats-signer-gate-safe-multisig-signing-authority.md](hats-signer-gate-safe-multisig-signing-authority.md)
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
