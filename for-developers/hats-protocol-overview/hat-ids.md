# Hat IDs

Hat IDs are uint256 bitmaps that create an "address" — more like an web or IP address than an Ethereum address — that includes information about the entire branch of admins for a given hat.

The 32 bytes of a hat's id are structured as follows:

* The first 4 bytes are reserved for the top hat id. Since top hat ids are unique across a given deployment of Hats Protocol, we can also think of them as the top level "domain" for a hat tree.
* Each of the next chunks of 16 bits refers to a single "Hat Level".

This means there are 15 total hat levels, beginning with the top hat at level 0 and going up to level 14.&#x20;

A hat at level 6 will have 6 admins in its branch of the tree, and therefore its id will have non-zero values at levels 0-5 as well as its own level. Since these values correspond to its admins, all that is needed to know which hats have admin authorities over a given hat is to know that given hat's id.

### **Hat Tree Space**

A hat tree can have up to 14 levels, plus the top hat (tree root). Within those 14 levels are 224 bits of address space (remember, one level contains 16 bits of space), so the maximum number of hats in a single hat tree is:

$$
2^{224} + 1 \approx ~2.696 * 10^{67}
$$

which is well beyond the number of stars in the universe.

### **Displaying Hat Ids**

It is recommended for front ends to instead convert hat ids to hexadecimal, revealing the values of the bytes — and therefore the hat levels — directly.

For example, instead of a hat id looking like this under base 10: `26960769438260605603848134863118277618512635038780455604427388092416`

...under hexadecimal it would look like this: `0x0000000100020003000000000000000000000000000000000000000000000000`

In this second version, you can see that this hat is...

* a level 2 hat
* is in the first hat tree (top hat id = 1)
* is the third hat created at level 2 within this tree
* admin'd by the second hat created at level 1 within this tree

We can also prettify this even further by separating hat levels with periods, a la IP addresses:

`0x00000001.0002.0003.0000.0000.0000.0000.0000.0000.0000.0000.0000.0000.0000.0000`
