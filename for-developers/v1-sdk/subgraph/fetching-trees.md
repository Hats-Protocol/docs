# Fetching Trees

### <mark style="color:purple;">getTree</mark>

Get a Tree by its ID.

```typescript
const tree = await hatsSubgraphClient.getTree({
    chainId,
    treeId,
    props,
    filters,
});
```

_**Arguments**_:

```typescript
{
    chainId: number;
    treeId: number;
    props: TreeConfig;
    filters?: Filters;
}
```

* `chainId` - ID of the chain to fetch from.
* `treeId` - ID of the Tree to fetch (Tree's top-hat domain - first 4 bytes of the top-hat ID).
* `props` - Tree's properties to fetch, including the ones of nested objects. Check the [TreeConfig](types.md#treeconfig) type for the available properties.
* `filters` - Optional filters to include in the GraphQL query. Check the [Filters](types.md#filters) type for the available filters.

_**Response**_:

```typescript
Tree
```

A [Tree object](types.md#tree), containing the chosen properties.

### <mark style="color:purple;">getTreesByIds</mark>

Get Trees by their IDs.

```typescript
const trees = await hatsSubgraphClient.getTreesByIds({
    chainId,
    treeIds,
    props,
    filters,
});
```

_**Arguments**_:

```typescript
{
    chainId: number;
    treeIds: number[];
    props: TreeConfig;
    filters?: Filters;
}
```

* `chainId` - ID of the chain to fetch from.
* `treeIds` - IDs of the Trees to fetch (Tree's top-hat domain - first 4 bytes of the top-hat ID).
* `props` - Tree's properties to fetch, including the ones of nested objects. Check the [TreeConfig](types.md#treeconfig) type for the available properties.
* `filters` - Optional filters to include in the GraphQL query. Check the [Filters](types.md#filters) type for the available filters.

_**Response**_:

```typescript
Tree[]
```

An array of [Tree objects](types.md#tree), containing the chosen properties.

### <mark style="color:purple;">getTreesPaginated</mark>

Paginate over Trees.

```typescript
const trees = await hatsSubgraphClient.getTreesPaginated({
    chainId,
    props,
    page,
    perPage,
    filters,
});
```

_**Arguments**_:

```typescript
{
    chainId: number;
    props: TreeConfig;
    page: number;
    perPage: number;
    filters?: Filters;
}
```

* `chainId` - ID of the chain to fetch from.
* `props` - Tree's properties to fetch, including the ones of nested objects. Check the [TreeConfig](types.md#treeconfig) type for the available properties.
* page - Number of page to fetch.
* perPage - Number of Trees to fetch in each page.
* `filters` - Optional filters to include in the GraphQL query. Check the [Filters](types.md#filters) type for the available filters.

_**Response**_:

```typescript
Tree[]
```

An array of [Tree objects](types.md#tree), containing the chosen properties.
