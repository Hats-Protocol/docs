# Hat Image URIs

Like any other NFT, hats have images. The image for a given hat is determined by the following logic:

1. If the hat's `imageURI` property is set, use that
2. If the hat's `imageURI` property is _not_ set, then use the `imageURI` of the hat's admin Hat
3. If the admin hat's `imageURI` property is _not_ set, then use the `imageURI` of _that_ hat's admin
4. Repeat (3) until you find an `imageURI` that is set
5. If no set `imageURI` is found within the original hat's hat tree (including the Top Hat), then use the `globalImageURI` set in the Hats Protocol contract

This logic creates flexibility for DAOs to efficiently customize images for their hats, while keeping images as optional and hat creation relatively cheap.
