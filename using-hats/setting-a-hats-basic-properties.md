# 🏗 Setting a Hat's Basic Properties

For each hat you create, the first type of properties you'll be able to edit are under the "Hat Basics" section:

<figure><img src="../.gitbook/assets/Hat Basics.png" alt=""><figcaption></figcaption></figure>

### Image

Like any other NFT, hats have images. You can set a specific image for each hat. If no image is set for a hat, it will adopt the image of its nearest admin, as seen in the hats with IDs 2.3.1, 2.4.1, and 2.5.1 below.

<figure><img src="../.gitbook/assets/Screenshot 2023-07-13 at 8.09.38 PM.png" alt=""><figcaption><p>A subset of the <a href="http://127.0.0.1:5000/u/Ajcq1GvbYJMa6t1IqqyyBN3Bewo2">Cabin</a> Hats tree</p></figcaption></figure>

### Name & Description

Free-text fields.&#x20;

Once set, the hat's name will be shown on its associated card in the tree graph. Additionally, once choosing the hat, its name and description are located at the top of the hat's sidebar.

<figure><img src="../.gitbook/assets/Name And Description.png" alt=""><figcaption></figcaption></figure>

### Editable (Mutability)

Mutability determines whether the hat's properties (including name, description, max supply, mutability, image, eligibility and toggle modules) can be changed by its admins. Additionally, mutable hats can be transferred by their admins to a different wearer. Immutable hats cannot be transferred.

Immutable hats cannot be made mutable later, so we generally recommend starting with mutable hats, with the option to make them immutable later once your organization's structure solidifies and there is a need to limit the powers of a hat's admins.

**Why make a hat immutable?** In some cases, a hat's properties should be immutable to give everybody (particularly the wearer(s)) maximal confidence in what they are signing up for. Immutability also curbs the powers of a hat's admins, as immutable hats cannot be changed or transferred by admins.

**Top Hat exception:** The only exception to the above mutability rules is for Top Hats, which despite being immutable are allowed to change their own `details` and `imageURI` (but not other properties). Note that this only includes non-linked Top Hats; a Top Hat that has been linked (aka grafted) onto another hat tree is no longer considered a Top Hat, and therefore is subject to the same mutability rules as other hats.
