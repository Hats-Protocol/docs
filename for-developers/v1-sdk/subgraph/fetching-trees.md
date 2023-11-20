# Fetching Trees

### <mark style="color:purple;">getTree</mark>

Get a Tree by its ID.

```typescript
const tree = await hatsSubgraphClient.getTree({
    chainId,
    treeId,
    props,
});
```

_**Arguments**_:

```typescript
{
    chainId: number;
    treeId: number;
    props: TreePropsConfig;
}
```

* `chainId` - ID of the chain to fetch from.
* `treeId` - ID of the Tree to fetch (Tree's top-hat domain - first 4 bytes of the top-hat ID).
* `props` - Tree's properties to fetch, including the ones of nested objects. Check the [TreePropsConfig](types.md#treepropsconfig) type for the available properties and query filters.

_**Response**_:

```typescript
Tree
```

A [Tree object](types.md#tree), containing the chosen properties.

_**Example:**_

```typescript
// get a tree's top-hat
const res = await client.getTree({
  chainId: 10, // optimism
  treeId: 1, 
  props: {
    hats: { // get the tree's hats
      props: {}, // for each hat, include only its ID
      filters: { first: 1 }, // fetch only the first hat (the top-hat)
    },
  },
});
```

### <mark style="color:purple;">getTreesByIds</mark>

Get Trees by their IDs.

```typescript
const trees = await hatsSubgraphClient.getTreesByIds({
    chainId,
    treeIds,
    props,
});
```

_**Arguments**_:

```typescript
{
    chainId: number;
    treeIds: number[];
    props: TreePropsConfig;
}
```

* `chainId` - ID of the chain to fetch from.
* `treeIds` - IDs of the Trees to fetch (Tree's top-hat domain - first 4 bytes of the top-hat ID).
* `props` - Tree's properties to fetch, including the ones of nested objects. Check the [TreePropsConfig](types.md#treepropsconfig) type for the available properties and query filters.

_**Response**_:

```typescript
Tree[]
```

An array of [Tree objects](types.md#tree), containing the chosen properties.

_**Example:**_&#x20;

```typescript
const res = await client.getTreesByIds({
  chainId: 10, // optimism
  treeIds: [1, 2],
  props: {
    hats: { // for each tree, fetch its hats
      props: {
        status: true, // for each hat, include its status (active/inactive)
      },
      filters: { first: 200 }, // fetch only the first 200 hats
    },
  },
});
```

### <mark style="color:purple;">getTreesPaginated</mark>

Paginate over Trees.

```typescript
const trees = await hatsSubgraphClient.getTreesPaginated({
    chainId,
    props,
    page,
    perPage,
});
```

_**Arguments**_:

```typescript
{
    chainId: number;
    props: TreePropsConfig;
    page: number;
    perPage: number;
}
```

* `chainId` - ID of the chain to fetch from.
* `props` - Tree's properties to fetch, including the ones of nested objects. Check the [TreePropsConfig](types.md#treepropsconfig) type for the available properties and query filters.
* page - Number of page to fetch.
* perPage - Number of Trees to fetch in each page.

_**Response**_:

```typescript
Tree[]
```

An array of [Tree objects](types.md#tree), containing the chosen properties.

_**Example:**_

```typescript
const res = await client.getTreesPaginated({
  chainId: 10, // optimism
  props: {
    hats: { // for each tree, get its hats
      props: {}, // for each hat, include only its ID 
      filters: { first: 1 }, // fetch only the first hat of every tree (the top-hat)
    },
  },
  page: 3, // get the third page
  perPage: 10, // each page contains 10 trees
});
```
