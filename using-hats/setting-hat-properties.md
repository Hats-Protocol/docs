---
description: Details, max supply, mutability, and image
---

# 🏗 Setting Hat Properties

For each hat you create you will need to determine its details, max supply, mutability, and image. Each of these properties can be changed by a hat's admins, unless the hat is immutable.

### Details

A hat's details contain metadata about the hat such as a name, description, and other properties like roles and responsibilities associated with the Hat.&#x20;

Text in the details field should not exceed 7,000 characters. However, you may also include links to external documents here; this approach may be especially useful if 1) the Hat has a particularly long description, 2) you'd like to update the hat's description frequently without requiring additional onchain transactions, and/or 3) you'd like to enable those beyond the hat's admins to make changes to its description.

### Max Supply

Max supply is the maximum number of addresses that can wear a given hat at once. Max supply could be set to 1 to ensure only one address is holding that role at a given time, or it could be set as high as 4.29 billion (2^32).&#x20;

### Mutability

Mutability determines whether the hat's properties (including name, description, max supply, mutability, image, and eligibility and toggle modules) can be changed by its admins. Additionally, mutable hats can be transferred by their admins to a different wearer. Immutable hats cannot be transferred.

Immutable hats cannot be made mutable later, so we generally recommend starting with mutable hats, with the option to make them immutable later once your organization's structure solidifies and there is a need to limit the powers of a hat's admins.

**Why make a hat immutable?** In some cases, a hat's properties should be immutable to give everybody (particularly the wearer(s)) maximal confidence in what they are signing up for. Immutability also curbs the powers of a hat's admins, as immutable hats cannot be changed or transferred by admins.

**Top Hat exception:** The only exception to the above mutability rules is for Top Hats, which despite being immutable are allowed to change their own `details` and `imageURI` (but not other properties). Note that this only includes non-linked Top Hats; a Top Hat that has been linked (aka grafted) onto another hat tree is no longer considered a Top Hat, and therefore is subject to the same mutability rules as other hats.

### Image

Like any other NFT, hats have images. You can set a specific image for each hat using an image URI (e.g., an ipfs hash or a link to an image stored on a website), or uploading the image directly into the [Hats app](https://app.hatsprotocol.xyz).

If no image is set for a hat, it will adopt the image of its nearest admin, as seen in the hats with IDs 2.3.1, 2.4.1, and 2.5.1 below.

<figure><img src="../.gitbook/assets/Screenshot 2023-07-13 at 8.09.38 PM.png" alt=""><figcaption><p>A subset of the <a href="http://127.0.0.1:5000/u/Ajcq1GvbYJMa6t1IqqyyBN3Bewo2">Cabin</a> Hats tree</p></figcaption></figure>
