# Hat IDs

Hat ids are semantic. They have meaning.

Hat ids uint256 bitmaps that create an "address" — more like an web or IP address than an Ethereum address — that includes information about where in the tree a hat is located, including its entire branch of admins.

The 32 bytes of a hat's id are structured as follows:

* The first 4 bytes are reserved for the top hat id. Since top hat ids are unique across a given deployment of Hats Protocol, we can also think of them as the top level "domain" for a hat tree.
* Each of the next chunks of 16 bits refers to a single "Hat Level".

There are 15 total hat levels, beginning with the top hat at level 0 and going up to level 14.

#### Example

Consider the following hat id (in hex): 0x<mark style="color:red;">0000000f</mark><mark style="color:blue;">00020005000a00010000000000000000000000000000000000000000</mark>

For convenience, we can reformat it into shorthand, just like an IP address: <mark style="color:red;">15</mark>.<mark style="color:blue;">2</mark>.<mark style="color:blue;">5</mark>.<mark style="color:blue;">10</mark>.<mark style="color:blue;">1</mark>

From the id alone, we know a lot about this hat:

* It is in hat tree 15
* It is a level 4 hat
* Its immediate admin (aka parent) is <mark style="color:red;">15</mark>.<mark style="color:blue;">2</mark>.<mark style="color:blue;">5</mark>.<mark style="color:blue;">10</mark>
* Its grandparent is <mark style="color:red;">15</mark>.<mark style="color:blue;">2</mark>.<mark style="color:blue;">5</mark>

#### Other hat id formats

<table><thead><tr><th width="146">Format</th><th>Example</th></tr></thead><tbody><tr><td>Integer ("raw")</td><td>6470400364654781217010529864562902351218663490360806944392503307010048</td></tr><tr><td>Hexadecimal</td><td>0x<mark style="color:red;">0000000f000200050000a00010000000000000000000000000000000000000000</mark></td></tr><tr><td>Hexadecimal with level delimiters</td><td>0x<mark style="color:red;">0000000f</mark>.<mark style="color:blue;">0002</mark>.<mark style="color:blue;">0005</mark>.<mark style="color:blue;">000a</mark>.<mark style="color:blue;">0001</mark>.<mark style="color:blue;">0000</mark>.<mark style="color:blue;">0000</mark>.<mark style="color:blue;">0000</mark>.<mark style="color:blue;">0000</mark>.<mark style="color:blue;">0000</mark>.<mark style="color:blue;">0000</mark>.<mark style="color:blue;">0000</mark>.<mark style="color:blue;">0000</mark>.<mark style="color:blue;">0000</mark>.<mark style="color:blue;">0000</mark><br><br>0x<mark style="color:red;">0000000f</mark>_<mark style="color:blue;">0002</mark>_<mark style="color:blue;">0005</mark>_<mark style="color:blue;">000a</mark>_<mark style="color:blue;">0001</mark>_<mark style="color:blue;">0000</mark>_<mark style="color:blue;">0000</mark>_<mark style="color:blue;">0000</mark>_<mark style="color:blue;">0000</mark>_<mark style="color:blue;">0000</mark>_<mark style="color:blue;">0000</mark>_<mark style="color:blue;">0000</mark>_<mark style="color:blue;">0000</mark>_<mark style="color:blue;">0000</mark>_<mark style="color:blue;">0000</mark></td></tr><tr><td>"IP address"</td><td><mark style="color:red;">15</mark>.<mark style="color:blue;">2</mark>.<mark style="color:blue;">5</mark>.<mark style="color:blue;">10</mark>.<mark style="color:blue;">1</mark></td></tr></tbody></table>

### **Hat Tree Space**

A hat tree can have up to 14 levels, plus the top hat (tree root). Within those 14 levels are 224 bits of address space (remember, one level contains 16 bits of space), so the maximum number of hats in a single hat tree is approximately:

$$
2^{224} + 1 \approx ~2.696 * 10^{67}
$$

which is well beyond the number of stars in the universe.
