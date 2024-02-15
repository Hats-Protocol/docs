---
description: So you received your first hat. Now what?
---

# 🤠 Essentials For Hat Wearers

### **Congratulations, you've received a hat!**

![](<../.gitbook/assets/Screenshot 2023-08-12 at 11.52.06 AM (1).png>)![](<../.gitbook/assets/Screenshot 2023-08-12 at 11.52.12 AM.png>)

We hope this hat gives you the context, authorities, and accountabilities you need to get things done.

## **What are hats?**

A hat is a "role in a box". More specifically, hats are programmable roles which can be imbued with responsibilities, [authorities](connecting-hats-with-authorities/), and accountabilities. [Roles](what-hats-do-i-need.md) can be big and ongoing, or small and discrete.&#x20;

<figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.53.33 AM.png" alt=""><figcaption></figcaption></figure>

## **What hats do I have?**

To learn what kind of hat(s) you have, visit the [Hats App](https://app.hatsprotocol.xyz), connect your wallet, and click My Hats.

<figure><img src="../.gitbook/assets/Screenshot 2023-08-14 at 4.25.08 PM.png" alt="" width="348"><figcaption><p>The My Hats page is your portal to accessing all your hats. If you don't see the My Hats link, be sure to connect to the app with the correct wallet address.</p></figcaption></figure>

You'll see all the hats your wallet address is holding in your My Hats page. Hats are ERC1155-compatible tokens that can be held by any address including an EOA or a contract (e.g. a multisig). When an address has a balance of 1 of a given Hats token, it is considered a "wearer" of that "hat".

## **What can my hats do?**

Hats often come with special [authorities](../hats-integrations/hat-gated-authorities/) which you can only access as long as you're wearing that hat. To see what authorities your hat grants you, click on the hat in your My Hats page. This will open up the full structure of hats (called a "Hats tree") within which your particular hat lives, along with a information panel for your hat.&#x20;

<figure><img src="../.gitbook/assets/image (2).png" alt="" width="300"><figcaption></figcaption></figure>

In this information panel you'll find lots of information about your hat, including a description for the hat, any responsibilities associated with the role, and any authorities you receive by wearing the hat. The links found in the authorities section will usually direct you to the right place to claim those authorities. If you do not see any way to claim the authorities associated with your hat, contact the group or person who sent you your hat.&#x20;

<figure><img src="../.gitbook/assets/Screenshot 2023-08-12 at 12.29.31 PM.png" alt=""><figcaption><p>An example authorities set provided <a href="https://app.hatsprotocol.xyz/trees/5/6?hatId=6.1.3.2.1">by the DemoDAO Community Member hat found here</a>, which you can permissionlessly claim to test out</p></figcaption></figure>

## **What else can my hat do?**

Your hat is an admin for any hats in the direct lineage below it.

<figure><img src="../.gitbook/assets/image (1) (1).png" alt="" width="375"><figcaption><p>Admin relationships</p></figcaption></figure>

As an admin, you can change a hat's name, image, description, max supply, authorities, and accountabilities, grant the hat to new wearers, and transfer the hat from one wearer to another -- but ONLY if the hat is [mutable](setting-a-hats-basic-properties.md#editable-mutability). When hats are immutable, your admin powers are diminished.

To see which hats your hat is an admin of, click on your hat in the My Hats page and take a look at the tree within which your hat exists.

You can find the hats you're wearing in this tree based on the little green hat icon seen in the hat cards. For example, in the image below, you would see that you are wearing the Product Workstream Facilitator hat 6.1.2.3 ([for more on hat IDs, see here](../for-developers/hats-protocol-overview/hat-ids.md)).&#x20;

<figure><img src="../.gitbook/assets/Screenshot 2023-08-12 at 12.45.09 PM.png" alt=""><figcaption></figcaption></figure>

As a wearer of hat 6.1.2.3 in the tree above, you are an admin for any hats in the direct lineage below it, including 6.1.2.3.1, 6.1.2.3.2, and 6.1.2.3.3.

Similarly, the hats that are direct ancestors of your hat have admin authority over your hat—unless, of course, your hat is immutable.

## **Can I transfer my hat?**

No. Hats are nontransferrable by the wearer. Hats can only be transferred or revoked by its [admin hats](setting-accountabilities/admins-creating-issuing-and-revising-hats.md) as well as the accountability addresses for your specific hat.&#x20;

Just like you can't transfer or sell your job online without your organization's approval, you can't transfer your hats unilaterally either.

<figure><img src="../.gitbook/assets/Group 57.png" alt=""><figcaption></figcaption></figure>

## **How do I keep this hat?**

To keep your hat, you'll need to fulfill whatever responsibilities are associated with your hat, as well as remain eligible according to [the accountabilities embedded in your hat](setting-accountabilities/eligibility-requirements-for-wearers.md). Accountabilities could include things like holding certain tokens or NFTs in your wallet, staking, winning an organizational election, or agreeing to specific conditions. If you don't follow these accountabilities, your hat could be manually or automatically revoked or deactivated.&#x20;

To see the accountabilities embedded in your hat, view your hat's information panel or contact your organization.

## **Can I create other hats?**

Yes! As a hat wearer you can also create new child hats -- these are new hats directly beneath yours that you can set up and manage however you wish.&#x20;

But take note! Any hats that are the admin of your hat will ALSO be the admin of the child hats you create. Additionally, if you are not the sole wearer of your hat (as hats can be worn by multiple addresses up to the [max supply](adding-wearers.md#max-wearers)), then any of the other wearers of your hat will also have admin powers over the child hat you created.&#x20;

If you'd rather ensure that you are the only admin over the hats you create, it's probably best [to create a new Hats tree](creating-my-first-hat.md) or create a new child hat that you then make immutable.

<figure><img src="../.gitbook/assets/image (2) (1).png" alt="" width="375"><figcaption><p>Your hat can create new child hats - but be aware who else has admin rights over that hat!</p></figcaption></figure>

## **What else do I need to know?**

Those are the basics. If you have other questions or are unsure of what a term means, visit the [Glossary & FAQ](glossary-and-faq.md).&#x20;

For everything else, you'll find the information you need in the docs found here or via the group that sent you your hat. And if that's not enough, you can always [get in touch with us here](https://hatsprotocol.typeform.com/getintouch), we're here to help.
