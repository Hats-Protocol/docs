---
description: >-
  How to propose changes in Edit Mode, export those changes to share with
  others, and deploy those changes through a multisig or DAO contract
---

# 🌳 Drafting, Exporting, and Deploying Tree Changes

Once a Hats tree has been [created](creating-my-first-hat.md#1.-creating-a-new-tree), you can use the app's Edit Mode to draft, share and/or deploy changes to the tree.&#x20;

## Drafting

Use [Edit Mode](creating-my-first-hat.md) to create new hats, give them a [name and image](setting-a-hats-basic-properties.md), [add wearers](adding-wearers.md), [specify powers & responsibilities](connecting-hats-w-permissions-and-authorities/documenting-hat-powers-and-responsibilities.md), add modules to automate hat [eligibility and revocation](setting-accountabilities/eligibility-requirements-for-wearers.md), enable [hat-claiming](making-hats-claimable.md) and more.&#x20;

In large tress, you can group hats together for a cleaner display by creating a parent hat with zero as its "max wearers" property.&#x20;

<figure><img src="../.gitbook/assets/Group Hat (1).png" alt=""><figcaption></figcaption></figure>

You can create as many new hats and changes to the Hats tree as you’d like before deploying all changes in one transaction.&#x20;

<figure><img src="https://lh7-us.googleusercontent.com/1fftIQh9W2kDYhOZSp1seaeN_PzP8Vi0o7fdm7hgaOS1esyxE5JjtZn3OFqzbq4KxvwYAp-rNbRNpZKRdBONL-Ad9nXCX52USWkXT5b6bJtGQ3jno4jddCAa0B_93IGKneaoFJG7tOw1JL14N26T2Ew" alt=""><figcaption><p>Use Edit Mode to draft, share, and deploy changes to your Hats tree</p></figcaption></figure>

## Deploying

After making changes in edit mode, you have the option to deploy the changes for which you have [admin authorities](setting-accountabilities/admins-creating-issuing-and-revising-hats.md)\*. If you are wearing the Top Hat, this means you'll be able to deploy all the changes immediately.

To deploy all other changes, you can:

1. Export and share your proposed edits with others, and&#x20;
2. Provide the transaction calldata necessary to deploy those changes onchain

Both of these options are described below.

_\*Each hat is an admin of all other hats linked directly below it. Therefore, wearers of certain hats will be able to deploy changes to other mutable hats for which their hat is an admin. This includes minting both mutable and immutable hats to new wearers, and transfer mutable hats from one address to another. For more information about Admins in a Hats tree, click_ [_here_](setting-accountabilities/admins-creating-issuing-and-revising-hats.md)_._

## Sharing

You can export the changes made in Edit Mode in order to share them with others. This is especially useful for sharing any changes for which you do not have the admin authority to deploy. &#x20;

There are two options:

1. Exporting a JSON file to save and share your changes with others.
2. Exporting transaction Call Data in order to use in an onchain proposal.

### Exporting & Importing a JSON to Share & View Changes

To share your suggested changes with others, click the “Export” button found in Edit Mode, as seen in the screenshot below. Others can then import this JSON file into the same tree to see all the changes you’ve created.&#x20;

<figure><img src="https://lh7-us.googleusercontent.com/HTP0014QPYzyHMq6-JkW4e571VT-dpMx9dBIwqYhIVVgIDE_EzZBqcDnQqQteARn0qR0Z781ExFN46DpLn8yIvy_huRfulj5WgyFFk4JicvRJLhBAzO6SDBm93JEudzt7ZefqfuiE3HtRqIm19VsmF0" alt=""><figcaption><p>Export and import changes to a tree using the buttons seen above</p></figcaption></figure>

### Exporting Call Data to Deploy Changes Onchain

To deploy changes via a DAO or multisig-controlled hat (e.g. a DAO contract wearing the top-hat), copy the transaction call data using the information found in edit mode as seen in the screenshot below.&#x20;

<figure><img src="https://lh7-us.googleusercontent.com/rqSJsl2uUqEfMtsobOUPDN7BC6VXdfJj6aEW1bq4dYK-WwoDCEWT8n2cPS7mcslg9OKB8Mfs8EAuj1Tedipq5zEaIpOVnAd7MmLLxyCuT7G4Hk5t1d9W6ar6o3yZCzCE2jxXcUykexKRDFHoy_OUJbs" alt=""><figcaption><p>Use transaction call data to deploy changes through a multisig or DAO contract</p></figcaption></figure>

You can then use your organization's governance interface to create a proposal, in which the target address is the [Hats contract address](connecting-hats-w-permissions-and-authorities/connecting-hats-to-token-gates/hats-protocol-contract-addresses.md) and with the transaction Call Data as copied from the app.&#x20;

We recommend including the associated JSON file in your proposal as well, so that others can review your changes directly within the Hats app by importing the JSON into the same tree and confirm the validity of the transaction.
