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
});
```

_**Arguments**_:

```typescript
{
    chainId: number;
    search: string;
    treeProps: TreePropsConfig;
    hatProps: HatPropsConfig;
    wearerProps: WearerPropsConfig;
}
```

* `chainId` - ID of the chain to fetch from.
* `search` - ID to search for (Hat ID or pretty ID, Tree ID or Wearer address).
* `treeProps` - Tree's properties to fetch, including the ones of nested objects. Check the [TreePropsConfig](types.md#treepropsconfig) type for the available properties and query filters.
* `hatProps` - Hat's properties to fetch, including the ones of nested objects. Check the [HatPropsConfig](types.md#hatpropsconfig) type for the available properties and query filters.
* `wearerProps` - Wearer's properties to fetch, including the ones of nested objects. Check the [WearerPropsConfig](types.md#wearerpropsconfig) type for the available properties and query filters.

_**Response**_:

```typescript
{ trees: Tree[]; hats: Hat[]; wearers: Wearer[] }
```

An object containing the search result.&#x20;

_**Example:**_

```typescript
// search for a given hat, tree or wearer.
// include only the object's ID in the reuslt 
const res = await client.searchTreesHatsWearers({
  chainId: 10,
  search: "0x0000000100020001000100000000000000000000000000000000000000000000",
  treeProps: {},
  hatProps: {},
  wearerProps: {},
});
```
