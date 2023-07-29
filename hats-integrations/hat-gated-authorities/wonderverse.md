---
description: How to hat-gate access to Wonderverse orgs and pods
---

# Wonderverse

**To hat-gate access to Wonderverse Orgs or Pods, complete the following steps:**

First, enter the **Org Settings** of your Wonderverse Org OR enter the **Pod Settings** for your Wonderverse Pod. The following instructions will be the same for each:

1. Creating a role
2. Adding a token gate
3. Inviting members

### 1. Creating a role

Select **Roles** in the lefthand navigation

Enter the name and authorities associated with this role and select **Create Role** (we recommend you create a role with the same name as the hat you intend to associate it with)

Scroll down and select **Add Token Gate**

<figure><img src="../../.gitbook/assets/Screenshot 2023-06-30 at 11.31.24 AM.png" alt=""><figcaption></figcaption></figure>

### 2. Adding a token gate

**Create a new token gate** associated with this role.

Enter the information relevant to the hat(s) you want to connect this authority to, including:

* Select the chain your hats are on
* Select "ERC1155" under "Token Type"
* Enter the Hats Protocol contract address ([found here](./)) under "Token"
* Enter "1" under "Min. amount to hold"
* Enter the Hats token ID associated with the hat you'd like to give this authority to
* Name the token gate (we recommend giving it the same name as the associated hat)

&#x20;_See_[#hats-protocol-contract-addresses-and-token-ids](./#hats-protocol-contract-addresses-and-token-ids "mention") _for details on how to find the Hats Protocol contract address and specific hat token IDs_.

Select **Create Token Gate**

<figure><img src="../../.gitbook/assets/Screenshot 2023-06-30 at 11.24.55 AM.png" alt=""><figcaption></figcaption></figure>

### **3. Inviting others to collect this Wonderverse role via the token gate**&#x20;

To invite people to join your Wonderverse using the token gate you created, select **Members** in the lefthand navigation, select **Invite**, and **select the role you created above** using the dropdown menu. **Copy the link found here**: this is the link you will use to invite addresses to join Wonderverse  and receive the specified role and associated authorities.

<figure><img src="../../.gitbook/assets/Screenshot 2023-06-30 at 12.13.26 PM.png" alt=""><figcaption></figcaption></figure>

That's it. You have now successfully hat-gated access to your Wonderverse Org or Pod, using the granular Wonderverse permissions set for that specific hat!
