# ERC1155 Compatibility

Hats Protocol conforms fully to the ERC1155 interface. All external functions required by the [ERC1155 standard](https://eips.ethereum.org/EIPS/eip-1155) are exposed by Hats Protocol. This is how hats can work out of the box with existing token-gating applications.

However, Hats Protocol is not fully compliant with the ERC1155 standard. Since hats are not transferable by their owners (aka "wearers"), there is little need for safe transfers and the `ERC1155TokenReceiver` logic.&#x20;

Developers building on top of Hats Protocol should note that mints and transfers of hats will not, for example, include calls to `onERC1155Received`.

To avoid confusion, Hats Protocol does not claim to be ERC1155-_compliant_. Instead, we say that Hats Protocol has "ERC1155-_similar_" tokens. When referring specifically to the ERC1155 _interface_, however, we do say that Hats Protocol conforms fully.
