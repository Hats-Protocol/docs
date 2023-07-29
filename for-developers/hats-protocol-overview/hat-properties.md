# Hat Properties

Every hat has several properties:

* `id` - the integer identifier for the hat, which also serves as the ERC1155-similar token id (see three paragraphs below)
* `details` - metadata about the hat; such as a name, description, and other properties like roles and responsibilities associated with the hat. Should not exceed 7,000 characters.
* `maxSupply` - the maximum number of addresses that can wear the Hat at once
* `admin` - the Hat that controls who can wear the hat
* `eligibility` - the address that controls eligibility criteria and whether a given wearer of the Hat is in good standing
* `toggle` - the address that controls whether the hat is active
* `mutable` - whether the hat's properties can be changed by the admin
* `imageURI` - the URI for the image used in the Hat's ERC1155-similar token. Should not exceed 7,000 characters.

For more information on each property, refer to the following detailed sections:

