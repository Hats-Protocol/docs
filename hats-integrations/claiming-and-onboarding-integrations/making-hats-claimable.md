---
description: Making hats claimable with a Multi Claims Hatter contract
---

# Multi Claims Hatter

In Hats Protocol, hats are typically issued by admins minting them to wearers. While often that is the desired behavior, there are cases where it is desirable to allow wearers to claim a hat themselves, assuming they are eligible to wear them.&#x20;

The Multi Claims Hatter (MCH) module can make multiple hats claimable. To do so, it has to be an admin of each of these hats. Thus, a claimable hat must have an admin hat that is worn by a MCH instance. One common option is creating a designated hat for it.

For example, if in normal operations a hat tree would look like this...

```
   +-------------+
   | 1) Top Hat  |
   +-------------+
        |
   +---------------+
   | 1.1) Role Hat |
   +---------------+  
```

... then to make the Role Hat claimable, and potentially any other hat, another hat needs to exist in between:

```
   +-------------+
   | 1) Top Hat  |
   +-------------+
        |
   +-----------------+
   | 1.1) Hatter Hat |
   +-----------------+
        |
   +---------------+
   | 1.2) Role Hat |
   +---------------+
```

Once the MCH instance wears this hat, it can make any hats that are under its branch as claimable.

The following guide will walk you through the steps required to make a hat claimable:

* Go to the tree that includes the hat you wish to make claimable
* Select "Edit Tree"
* Locate and select the hat
* Open the "Revocation & Eligibility" section

<figure><img src="../../.gitbook/assets/Revocation And Eligibility Zoom.png" alt=""><figcaption></figcaption></figure>

* Choose "Automatically" and then choose "Create new Module". This will open the module creation form

If a MCH instance has not been created yet, then you'll be able to create and choose the admin hat that will wear it.

<figure><img src="../../.gitbook/assets/Make Hat Claimable 1.png" alt=""><figcaption></figcaption></figure>

Now choose "Deploy & Return" to deploy the module and return to the hat edit form. The edit form will be automatically updated with the necessary changes, including minting the admin hat to the new MCH instance. Then, you'll be able to keep editing the tree and deploy when ready.

Otherwise, if a MCH instance has been already created, simply register the hat with the existing one.

<figure><img src="../../.gitbook/assets/Make Hat Claimable 2.png" alt=""><figcaption></figcaption></figure>
