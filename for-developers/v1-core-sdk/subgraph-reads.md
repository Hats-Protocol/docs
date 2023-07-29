# Subgraph Reads

Subgraph operations are currently supported for the following chains:

* Mainnet
* Optimism
* Polygon
* Gnosis Chain
* Arbitrum
* Goerli

If the chain ID does not match one of the networks above, then calling the following functions will throw a `SubgraphNotUpportedError` error.

More information on the Hats-Protocol subgraphs is included [here](../v1-subgraphs.md).

### <mark style="color:purple;">gqlGetHatsOfTree</mark>

Get all hats of a tree.

```typescript
const hats = await hatsClient.gqlGetHatsOfTree(treeId);
```

_**Arguments**_:

```typescript
treeId: number
```

`treeId` - The tree domain (first four bytes of the tree's tophat ID). &#x20;

_**Response**_:

```typescript
bigint[]
```

An array with all the tree's hat IDs.

### <mark style="color:purple;">gqlGetHatsOfWearer</mark>

Get all hats that an address currently wears.

**Note**: This function returns the hats that were minted to the wearer and that have not been burned. It does not check whether those hats are currently active or whether the wearer is currently eligible for the hat. Use the [`isWearerOfHat`](subgraph-reads.md#iswearerofhat) function in order to get the updated state.

```typescript
const hats = await hatsClient.gqlGetHatsOfWearer(wearer);
```

_**Arguments**_:

```typescript
wearer: Address
```

`wearer` - The wearer's address.

_**Response**_:

```typescript
bigint[]
```

An array of hat IDs.

### <mark style="color:purple;">gqlGetWearersPerHatInTree</mark>

Get a mapping of wearers per hat, for every hat in a given tree.

**Note**: This function returns the hats that were minted to every wearer and that have not been burned. It does not check whether those hats are currently active or whether the wearer is currently eligible for the hat. Use the [`isWearerOfHat`](subgraph-reads.md#iswearerofhat) function in order to get the updated state.

```typescript
const wearersPerHat = await hatsClient.gqlGetWearersPerHatInTree(treeId);
```

_**Arguments**_:

```typescript
treeId: number
```

`treeId` - The tree domain (first four bytes of the tree's tophat ID). &#x20;

_**Response**_:

```typescript
{ hatId: bigint; hatWearers: string[] }[]
```

For every hat, an object containing:

* hatId - the hat's ID.
* hatWearers - addresses of the hat's wearers.

### <mark style="color:purple;">gqlGetWearersOfHat</mark>

Get all wearers of a hat.

**Note**: This function returns the wearers which this hat was minted to and that have not been burned. It does not check whether the hat is currently active or whether the wearer is currently eligible for the hat. Use the [`isWearerOfHat`](subgraph-reads.md#iswearerofhat) function in order to get the updated state.

```typescript
const wearers = await hatsClient.gqlGetWearersOfHat(hatId);
```

_**Arguments**_:

```typescript
hatId: bigint
```

`hatId` - The hat's ID. &#x20;

_**Response**_:

```typescript
string[]
```

Addresses of the hat's wearers.

### <mark style="color:purple;">gqlGetHatsInBranch</mark>

Get all hats of a particular branch of the tree.

```typescript
const hats = await hatsClient.gqlGetHatsInBranch(rootHatId);
```

_**Arguments**_:

```typescript
rootHatId: bigint
```

`rootHatId` - Hat ID of the branch root. &#x20;

_**Response**_:

```typescript
bigint[]
```

Hat IDs of all hats in the branch, including the root.

