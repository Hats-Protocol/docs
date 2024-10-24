---
description: >-
  Provide subscription- or membership-based access to specific roles and
  permissions
---

# Subscription or Membership Fee (Unlock Protocol)

**Overview**

Hats has integrated with Unlock Protocol to allow organizations to set up recurring subscriptions or one-time membership fees for roles. When you add a subscription or membership fee to a role, a unique claim page is automatically generated for fee collection and onboarding.

Once a subscription or membership is active, the new member immediately gains all associated role powers, such as access to workspaces, communication channels, and voting rights. If the subscription is canceled or expires, access is automatically revoked.

The module's code is open source and is available [here](https://github.com/Hats-Protocol/unlock-eligibility).

### **Video guide** <a href="#adding-the-module-to-a-hat" id="adding-the-module-to-a-hat"></a>

{% embed url="https://www.loom.com/share/3213807bf3ed4b00a6e856a59a5661eb" %}

### **Adding the module to a hat** <a href="#adding-the-module-to-a-hat" id="adding-the-module-to-a-hat"></a>

* Go to the tree that includes the hat you wish to create the module for
* Select "Edit Tree"
* Locate and select the hat
* Open the "Revocation & Eligibility" section

<figure><img src="../../.gitbook/assets/Screenshot 2024-10-22 at 4.02.30 PM.png" alt=""><figcaption></figcaption></figure>

* Choose "Add Module". This will open the module creation form
* Choose "Subscription Eligibility (Unlock Protocol v14)" in the module type

<figure><img src="../../.gitbook/assets/Screenshot 2024-10-22 at 4.03.09 PM.png" alt=""><figcaption></figcaption></figure>

* Fill in the module-specific parameters, shown below.
  * **Withdrawing funds:** the Lock Manager address will be authorized to withdraw funds via [app.unlock-protocol.com/locks\
    ](https://app.unlock-protocol.com/locks).
  * **One-time purchase:** Turn the subscription into a one-time purchase by setting the subscription period to 10 or more years
* Choose "Deploy & Return" to deploy the module and return to the hat edit form. The module address will be automatically updated on the hat's eligibility property in the form. Once you deploy these changes, the hat's eligibility will be updated.

<figure><img src="../../.gitbook/assets/Screenshot 2024-10-22 at 4.06.34 PM.png" alt=""><figcaption></figcaption></figure>

**ONE MORE IMPORTANT STEP!** Copy the address that has now appeared in the hat's eligibility address as shown below. This is the address of the module you just deployed.&#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2024-10-23 at 4.13.12 PM.png" alt=""><figcaption></figcaption></figure>

Next, mint any hat that is an admin of the subscription-connected hat to this address. Do so by adding the module address you copied as a wearer of an admin hat (you may have to increase the max supply of this admin hat), and click save.

<figure><img src="../../.gitbook/assets/Screenshot 2024-10-23 at 4.16.58 PM.png" alt=""><figcaption></figcaption></figure>

Finally, deploy all your changes onchain.

### Sharing the Subscription/Fee Payment Page <a href="#viewing-the-hats-eligibility-criteria" id="viewing-the-hats-eligibility-criteria"></a>

Once deployed, exit from edit mode and return to the hat that you have added this subscription eligibility module to. In the hat's details, you will now see a "Pay the subscription" link.

<figure><img src="../../.gitbook/assets/Screenshot 2024-10-22 at 4.10.13 PM.png" alt=""><figcaption></figcaption></figure>

Follow this link to see a unique claim page that is automatically generated for fee collection and onboarding.

Once a subscription or membership is active, the new member automatically claims the hat and immediately gains all associated role powers, such as access to workspaces, communication channels, and voting rights. If the subscription is canceled or expires, access is automatically revoked.

<figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

### Withdrawing Collected Fees <a href="#viewing-the-hats-eligibility-criteria" id="viewing-the-hats-eligibility-criteria"></a>

Subscription or membership fees collected by the claim page above can be collected by visiting the Unlock Protocol app at [https://app.unlock-protocol.com/locks\
](https://app.unlock-protocol.com/locks), connecting your wallet, and withdrawing funds, as shown below.&#x20;

Unlock Protocol and Hats Protocol take a combined 1% protocol and 5% referral fee, respectively, to support the cost of development.

<figure><img src="../../.gitbook/assets/Screenshot 2024-10-24 at 1.18.18 PM.png" alt=""><figcaption></figcaption></figure>

