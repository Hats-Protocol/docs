---
description: >-
  How to hat-gate access to specific Charmverse roles, pages, and
  read/comment/write/admin permissions
---

# Charmverse

[Charmverse](https://charmverse.io) is a Web3 platform that provides Notion-like workspaces, databases, a forum, bounty system, and proposal system, all of which can be accessible only to wearers of specific hats using Charmverse's highly-customizable roles and permissions system.

There are three steps to connecting Charmverse permissions with specific hats.

1. Create a Charmverse role associated with your desired hat(s)
2. Set page-level permissions for that Charmverse role
3. Hat-gate access to that Charmverse role

Each step is explained in detail below.

## Step 1. Create a Charmverse role associated with your desired hat(s)

To set up your hat-gated authorities within Charmverse, first navigate to your Charmverse space, open "Settings", and select "Roles & Permissions".

<figure><img src="../../.gitbook/assets/Screenshot 2023-06-12 at 5.04.46 PM.png" alt=""><figcaption></figcaption></figure>

Next, select "Add a role" as seen in the lower-right of the screenshot above.

Create a Charmverse role you want to associate with a given hat or set of hats (you can associate multiple hats with a single Charmverse role). Enter a name for the role, do **not** add any members to the role, and select "Create role".

<figure><img src="../../.gitbook/assets/Screenshot 2023-06-12 at 5.06.40 PM.png" alt=""><figcaption></figcaption></figure>

Once the Charmverse role has been created, open the role with the dropdown arrow, select "Permissions", and set your desired permissions associated with this role.

<figure><img src="../../.gitbook/assets/Screenshot 2023-06-12 at 5.09.29 PM.png" alt=""><figcaption></figcaption></figure>

## Step 2. Set page-level permissions for that Charmverse role

Next, navigate to any Charmverse pages within your space that you specifically want to set permissions for. Each page within Charmverse can set its own permissions along the dimensions of view, view & comment, editor, and full access. **Note: subpages will inherit permissions from their parents.**

Once on a page, navigate to the "Share" button in the upper-right, and click in the box that says "Add people, roles or email"

<figure><img src="../../.gitbook/assets/Screenshot 2023-06-12 at 5.17.48 PM.png" alt="" width="375"><figcaption></figcaption></figure>

In the box that appears (shown below), set the permissions for this page, and add the role(s) you created into the "Roles" box. Then click "Invite".&#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2023-06-12 at 5.15.15 PM.png" alt="" width="375"><figcaption></figcaption></figure>

Repeat this process for all the Charmverse pages you want to make accessible to holder of the role(s) you created (remember, subpages will inherit permissions from their parents).

## 3. Hat-gate access to that Charmverse role

To require an address to be wearing a given hat in order to claim a Charmverse role, and the permissions held by that role, return to your Charmverse space's "Settings", select "Invites", select "Add", and click "Add a Token Gate"

<figure><img src="../../.gitbook/assets/Screenshot 2023-06-12 at 5.24.42 PM.png" alt=""><figcaption></figcaption></figure>

Selecet "Communities":

<figure><img src="../../.gitbook/assets/Screenshot 2024-04-02 at 13.45.06.png" alt="" width="563"><figcaption></figcaption></figure>

Select the blockchain network your hats are on and enter the Hats token ID associated with a hat you want to associate with this role (see [finding-a-hats-token-id.md](../../using-hats/connecting-hats-w-permissions-and-authorities/connecting-hats-to-token-gates/finding-a-hats-token-id.md "mention") _for details on how to find specific hat token IDs)_.

<figure><img src="../../.gitbook/assets/Screenshot 2024-04-02 at 13.48.35.png" alt="" width="563"><figcaption></figcaption></figure>

Then click "Next", review your condition and select "Confirm".

Finally, locate this new "Token Gated Link" within the Invites page, and assign the role you created to this token ID.&#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2023-07-21 at 1.48.13 PM.png" alt=""><figcaption></figcaption></figure>

Repeat this process for any other hats you want to associate with this same Charmverse role, or other roles you have created.

You can now select "Copy Link" associated with this Token Gated Link, which can be shared with wearers of the appropriate hat(s) to claim their Charmverse role and access the associated Charmverse permissions.
