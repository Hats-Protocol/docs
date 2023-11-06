# Misc

### <mark style="color:purple;">searchTreesHatsWearers</mark>

Search for a Hat, Tree or Wearer by ID.

```typescript
const res = await hatsSubgraphClient.searchTreesHatsWearers({
    chainId,
    search,
    treeProps,
    hatProps,
    wearerProps,
    filters,
});
```

_**Arguments**_:

```typescript
{
    chainId: number;
    search: string;
    treeProps: TreeConfig;
    hatProps: HatConfig;
    wearerProps: WearerConfig;
    filters?: Filters;
}
```

* `chainId` - ID of the chain to fetch from.
* `search` - ID to search for (Hat ID or pretty ID, Tree ID or Wearer address).
* `treeProps` - Tree's properties to fetch, including the ones of nested objects. Check the [TreeConfig](types.md#treeconfig) type for the available properties.
* `hatProps` - Hat's properties to fetch, including the ones of nested objects. Check the [HatConfig](types.md#hatconfig) type for the available properties.
* `wearerProps` - Wearer's properties to fetch, including the ones of nested objects. Check the [WearerConfig](types.md#wearerconfig) type for the available properties.
* `filters` - Optional filters to include in the GraphQL query. Check the [Filters](types.md#filters) type for the available filters.

_**Response**_:

```typescript
{ trees: Tree[]; hats: Hat[]; wearers: Wearer[] }
```

An object containing the search result.&#x20;
