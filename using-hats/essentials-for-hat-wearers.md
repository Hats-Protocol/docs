---
description: So you received your first hat. Now what?
---

# 🤠 Essentials For Hat Wearers

### **Congratulations, you've received a hat!**

![](<../.gitbook/assets/Screenshot 2023-08-12 at 11.52.06 AM (1).png>)![](<../.gitbook/assets/Screenshot 2023-08-12 at 11.52.12 AM.png>)

We hope this hat gives you the context, authorities, and accountabilities you need to get things done.

### **What are hats, you say?**

At their core, hats are programmable roles which can be imbued with responsibilities, [authorities](connecting-hats-with-authorities/), and [accountabilities](setting-accountabilities/). [Roles](what-hats-do-i-need.md) can be big and ongoing, or small and discrete.&#x20;

To learn what kind of hat you have, visit the [Hats App](https://app.hatsprotocol.xyz), connect your wallet, and click My Hats.

<figure><img src="../.gitbook/assets/Screenshot 2023-08-12 at 12.01.25 PM.png" alt="" width="346"><figcaption><p>The My Hats page is your portal to accessing all your hats. If you don't see the My Hats link, be sure to connect to the app with the right wallet address and on the right networks.</p></figcaption></figure>

You'll see all the hats your wallet address is holding in your My Hats page. Hats are ERC1155-compatible tokens that can be held by any address including an EOA, multisig, or contract. When an address has a balance of 1 of a given Hats token, it is considered a "wearer" of that "hat".

### **Now that you have a hat, you might be wondering... what can this hat do?**

Hats often come with special [authorities](../hats-integrations/hat-gated-authorities/) which you can only access as long as you're wearing that hat. To see what authorities your hat grants you, click on the hat in your My Hats page. This will open up the full structure of hats (called a "Hats tree") within which your particular hat lives, along with a information panel for your hat.&#x20;

<figure><img src="../.gitbook/assets/image.png" alt="" width="300"><figcaption></figcaption></figure>

In this information panel you'll find lots of information about your hat, including a description for the hat, any responsibilities associated with the role, and any authorities you receive by wearing the hat. The links found in the authorities section will usually direct you to the right place to claim those authorities. If you do not see any way to claim the authorities associated with your hat, contact the group or person who sent you your hat.&#x20;

<figure><img src="../.gitbook/assets/Screenshot 2023-08-12 at 12.29.31 PM.png" alt=""><figcaption><p>An example authorities set provided <a href="https://app.hatsprotocol.xyz/trees/5/6?hatId=6.1.3.2.1">by the DemoDAO Community Member hat found here</a>, which you can permissionlessly claim to test out</p></figcaption></figure>

### **What else can my hat do?**

Your hat can also edit other hats for which it is an admin, as well as create new child hats that you can [attach to specific authorities](connecting-hats-with-authorities/) and [send to new wearers](adding-wearers.md).

Click on your hat in the My Hats page and take a look at the Hats tree within which your hat exists.

You can find the hats you're wearing in this tree based on the little green hat icon seen in the hat cards. For example, in the image below, yours truly is wearing the Product Workstream Facilitator hat in the upper-right, with the hat ID 6.1.2.3 ([for more on hat IDs, see here](../for-developers/hats-protocol-overview/hat-ids.md)).&#x20;

<figure><img src="../.gitbook/assets/Screenshot 2023-08-12 at 12.45.09 PM.png" alt=""><figcaption></figcaption></figure>

As a wearer of hat 6.1.2.3, you are an admin for any hats in the direct lineage below it, including 6.1.2.3.1, 6.1.2.3.2, and 6.1.2.3.3.

<figure><img src="../.gitbook/assets/image (1).png" alt="" width="375"><figcaption><p>Admin relationships</p></figcaption></figure>

Admins can edit a hat's name, image, description, max supply, authorities, and accountabilities, grant the hat to new wearers, and transfer the hat from one wearer to another -- but ONLY if the hats are [mutable](setting-hat-properties.md#mutability). When hats are [immutable](setting-hat-properties.md#mutability), your admin powers are diminished.

### **Can I create other hats?**

Yes! As a hat wearer you can also create new child hats -- these are new hats directly beneath yours that you can set up and manage however you wish.&#x20;

But take note! Any hats that are the admin of your hat will ALSO be the admin of the child hats you create. Additionally, if you are not the sole wearer of your hat (as hats can be worn by multiple addresses up to the [max supply](setting-hat-properties.md#max-supply)), then any of the other wearers of your hat will also have admin powers over the child hat you created.&#x20;

If you'd rather ensure that you are the only admin over the hats you create, it's probably best [to create a new Hats tree](creating-my-first-hat.md) or create a child hat that you then make immutable.

<figure><img src="../.gitbook/assets/image (2).png" alt="" width="375"><figcaption><p>Your hat can create new child hats - but be aware who else has admin rights over that hat!</p></figcaption></figure>

### **Can I transfer my hat?**

No. Hats are nontransferrable by the wearer. Hats can only be transferred or revoked by designated [admin hats](setting-accountabilities/admins-creating-issuing-and-revising-hats.md) as well as the [accountability addresses](setting-accountabilities/) for your specific hat. Just like you can't transfer or sell your job online without your organization's approval, you can't transfer your hats unilaterally either.

<figure><img src="../.gitbook/assets/Group 57.png" alt=""><figcaption></figcaption></figure>

### **How do I keep this hat?**

To keep your hat, you'll need to fulfill whatever responsibilities are associated with your hat, as well as remain eligible according to [the accountabilities embedded in your hat](setting-accountabilities/eligibility-requirements-for-wearers.md). Accountabilities could include things like holding certain tokens or NFTs in your wallet, staking, winning an organizational election, or agreeing to specific conditions. If you don't follow these accountabilities, your hat could be manually or automatically revoked or deactivated.&#x20;

To see the accountabilities embedded in your hat, view your hat's information panel or contact your organization.

### **What else do I need to know?**

Those are the basics. If you have other questions or are unsure of what a term means, visit the [Glossary & FAQ](glossary-and-faq.md).&#x20;

For everything else, you'll find the information you need in the docs found here or via the group that sent you your hat. And if that's not enough, you can always [get in touch with us here](https://hatsprotocol.typeform.com/getintouch), we're here to help.
