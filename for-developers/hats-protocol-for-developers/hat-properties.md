---
description: The atomic unit of Hats Protocol is a hat.
---

# Hat Properties

Every hat has several properties:

* `id` - the integer identifier for the hat, which also serves as the [ERC1155-similar](erc1155-compatibility.md) token id
* `details` - arbitrary metadata about the hat; such as a name, description, and other properties like roles and responsibilities associated with the hat. Should not exceed 7,000 characters.
* `maxSupply` - the maximum number of addresses that can [wear](wearing-a-hat.md) the Hat at once
* `admin` - the hat that can issue the hat to wearers and can its hat's other properties
* `eligibility` - the address that controls eligibility criteria and whether a given wearer of the hat is in good standing
* `toggle` - the address that controls whether the hat is active
* `mutable` - whether the hat's properties can be changed by its admin
* `imageURI` - the URI for the image used in the Hat's ERC1155-similar token. Should not exceed 7,000 characters.

Refer to the subsequent sections for more information on each property.



