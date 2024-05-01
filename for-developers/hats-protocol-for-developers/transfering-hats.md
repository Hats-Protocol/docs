# Transfering Hats

Only a hat's admin can transfer its token(s) to new wearer(s).

Unlike typical tokens, the wearer of a hat cannot transfer the hat to another wallet. This is because the authorities and responsibilities associated with a hat are delegated to, not owned by, the wearer.

As a result, there is no need for safe transfers (transfers which check whether the recipient supports ERC1155) or to pass data to recipient `on1155Received` or `onERC1155BatchReceived` hooks.

For these reasons, in Hats Protocol, the standard ERC1155 transfer functions — `safeTransferFrom` and `safeBatchTransferFrom` are disabled and will always revert. Similarly, token approvals are not required and `setApprovalForAll` will always revert. See more about Hats Protocol and ERC1155 Compatibility here:

{% content-ref url="erc1155-compatibility.md" %}
[erc1155-compatibility.md](erc1155-compatibility.md)
{% endcontent-ref %}

As a replacement, hats can be transferred by admins via `Hats.transferHat`, which emits the ERC1155 standard event `TransferSingle`. Transfer recipients must not already be wearing the hat, and must be eligible to wear the hat.

With the exception of Top Hats — which can always transfer themselves — only mutable and active hats can be transferred.
