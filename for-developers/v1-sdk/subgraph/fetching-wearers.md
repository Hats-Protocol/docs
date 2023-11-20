# Fetching Wearers

### <mark style="color:purple;">getWearer</mark>

Get a Wearer by its address.

```typescript
const wearer = await hatsSubgraphClient.getWearer({
    chainId,
    wearerAddress,
    props,
});
```

_**Arguments**_:

```typescript
{
    chainId: number;
    wearerAddress:`0x${string}`;
    props: WearerPropsConfig;
}
```

* `chainId` - ID of the chain to fetch from.
* `wearerAddress` - Wearer's address.
* `props` - Wearer's properties to fetch, including the ones of nested objects. Check the [WearerPropsConfig](types.md#wearerpropsconfig) type for the available properties and query filters.

_**Response**_:

```typescript
Wearer
```

A [Wearer object](types.md#wearer), containing the chosen properties.

_**Example:**_

```typescript
const res = await client.getWearer({
  chainId: 10, // optimism
  wearerAddress: "0x1230000000000000000000000000000000000000",
  props: {
    currentHats: { // get the wearer's hats
      props: {
        status: true, // for each hat, include its status (active/inactive)
      },
    },
    mintEvent: { // get the wearer's hat minting events
      props: {
        blockNumber: true, // for each event, include its block number
      },
      filters: {
        first: 1, // fetch only the latest event
      },
    },
  },
});
```

### <mark style="color:purple;">getWearersOfHatPaginated</mark>

Paginate over the Wearers of a Hat.

```typescript
const wearers = await hatsSubgraphClient.getWearersOfHatPaginated({
    chainId,
    hatId,
    props,
    page,
    perPage,
});
```

_**Arguments**_:

```typescript
{
    chainId: number;
    hatId: bigint;
    props: WearerPropsConfig;
    page: number;
    perPage: number;
}
```

* `chainId` - ID of the chain to fetch from.
* `hatId` - ID of the hat of which wearers to fetch.
* `props` - Wearer's properties to fetch, including the ones of nested objects. Check the [WearerPropsConfig](types.md#wearerpropsconfig) type for the available properties and query filters.
* `page` - Number of page to fetch.
* `perPage` - Number of Wearers to fetch in each page.

_**Response**_:

```typescript
Wearer[]
```

An array of  [Wearer objects](types.md#wearer), containing the chosen properties.

_**Example:**_

```typescript
// get the first 10 wearers of a given hat
const res = await client.getWearersOfHatPaginated({
  chainId: 10,
  props: {}, // for each wearer, include only its ID (address)
  hatId: BigInt("0x0000000100020001000100000000000000000000000000000000000000000000"),
  page: 0,
  perPage: 10,
});
```
