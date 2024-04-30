---
description: >-
  How to hat-gate read, write, or comment access on specific Google docs,
  sheets, or slides
---

# Google Workspace

To hat-gate read, comment, or write access to specific Google documents, sheets, or slides, you will need to complete the following steps:

1. **Create a** [**Guild**](discord/guild.xyz-greater-than-discord.md) **role** associated with access to the Google Workspace document or use an existing Guild role
2. **Associate that Guild role with one or more Hats**
3. **Give that Guild role access** to the relevant Google document(s)

### **1. Create a new role in Guild or use an existing Guild role**&#x20;

_If you have not yet set up a Guild,_ [_follow these instructions_](https://help.guild.xyz/en/articles/6947591-how-to-gate-a-google-file)_._

Navigate to your existing Guild and select "Add Role". We recommend creating a Guild role with the same name and image as the Hat you want to associated it with.

If you have already created a Guild role that you want to associate with this authority, continue to step 2.

<figure><img src="../../.gitbook/assets/Screenshot 2023-07-21 at 1.57.11 PM.png" alt=""><figcaption></figcaption></figure>

### **2. Add a requirement that an address must hold a specific Hat token ID in order to claim that Guild role:**&#x20;

_If you have already associated that Guild role with the Hat token ID, you can skip this step._

Within that Guild role, select "Add Requirement"

<div align="left">

<figure><img src="../../.gitbook/assets/Guild add requirement.png" alt="" width="375"><figcaption></figcaption></figure>

</div>

Then select "NFT"

![](<../../.gitbook/assets/Guild select NFT.png>)



Next, input the chain your hat is on, add the Hats Protocol contract address, select "Custom ID" under Requirement type, and enter the custom token ID associated with the hat. _See_ [#hats-protocol-contract-addresses-and-token-ids](./#hats-protocol-contract-addresses-and-token-ids "mention") _for details on how to find the Hats Protocol contract address and specific hat token IDs_.

![](<../../.gitbook/assets/Guild add NFT requirement.png>)

Finally, select "Add requirement".&#x20;

This Guild role is now gated by the hat!

### **3. Give that Guild role access to the relevant Google document(s)**

Within the Guild role, select "Add Reward", select "Google Workspace", and follow the instructions to provide Guild with editor access to the appropriate Google document.&#x20;

Return to Guild, and wait a few seconds for the box below to appear. Once it does, select **Gate File** and then select the desired **access type.** Save by clicking **Gate file** again, and finally click **Save** once more to save the changes to the Guild role.

<figure><img src="../../.gitbook/assets/Screenshot 2023-06-29 at 5.37.28 PM.png" alt=""><figcaption></figcaption></figure>

That's it, you've now given specific hats special access to a Google Workspace document!&#x20;

### 4. Update your Hats tree to automatically include Guild authorities

This step will enable the Hats app to automatically detect and display Guild.xyz related authorities in your Hats tree:

{% hint style="info" %}
Skip this step if your tree's top-hat already includes the relevant Guild(s).
{% endhint %}

* Select "Edit Tree"
* Locate and select the tree's top-hat
* In the "Hat Basics" section, add the relevant Guilds. A Guild's name can be found in its URL. For example, if the Guild page is https://guild.xyz/hats-protocol, then its name is 'hats-protocol'.

<figure><img src="../../.gitbook/assets/Screenshot 2024-04-10 at 11.09.17.png" alt=""><figcaption></figcaption></figure>

Guild.xyz authorities will now be displayed on the relevant hats:

<figure><img src="../../.gitbook/assets/Screenshot 2024-04-10 at 11.58.09.png" alt="" width="563"><figcaption></figcaption></figure>
