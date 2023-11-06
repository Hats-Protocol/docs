# Fetching Wearers

### <mark style="color:purple;">getWearer</mark>

Get a Wearer by its address.

```typescript
const wearer = await hatsSubgraphClient.getWearer({
    chainId,
    wearerAddress,
    props,
    filters,
});
```

_**Arguments**_:

```typescript
{
    chainId: number;
    wearerAddress:`0x${string}`;
    props: WearerConfig;
    filters?: Filters;
}
```

* `chainId` - ID of the chain to fetch from.
* `wearerAddress` - Wearer's address.
* `props` - Wearer's properties to fetch, including the ones of nested objects. Check the [WearerConfig](types.md#wearerconfig) type for the available properties.
* `filters` - Optional filters to include in the GraphQL query. Check the [Filters](types.md#filters) type for the available filters.

_**Response**_:

```typescript
Wearer
```

A [Wearer object](types.md#wearer), containing the chosen properties.

### <mark style="color:purple;">getWearersOfHatPaginated</mark>

Paginate over the Wearers of a Hat.

```typescript
const wearers = await hatsSubgraphClient.getWearersOfHatPaginated({
    chainId,
    hatId,
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
    hatId: bigint;
    props: WearerConfig;
    page: number;
    perPage: number;
    filters?: Filters;
}
```

* `chainId` - ID of the chain to fetch from.
* `hatId` - ID of the hat of which wearers to fetch.
* `props` - Wearer's properties to fetch, including the ones of nested objects. Check the [WearerConfig](types.md#wearerconfig) type for the available properties.
* `page` - Number of page to fetch.
* `perPage` - Number of Wearers to fetch in each page.
* `filters` - Optional filters to include in the GraphQL query. Check the [Filters](types.md#filters) type for the available filters.

_**Response**_:

```typescript
Wearer[]
```

An array of  [Wearer objects](types.md#wearer), containing the chosen properties.
