# Fetching Hats

### <mark style="color:purple;">getHat</mark>

Get a Hat by its ID.

```typescript
const hat = await hatsSubgraphClient.getHat({
    chainId,
    hatId,
    props,
});
```

_**Arguments**_:

```typescript
{
    chainId: number;
    hatId: bigint;
    props: HatPropsConfig;
}
```

* `chainId` - ID of the chain to fetch from.
* `hatId` - ID of the Hat to fetch.
* `props` - Hat's properties to fetch, including the ones of nested objects. Check the [HatPropsConfig](types.md#hatpropsconfig) type for the available properties and query filters.

_**Response**_:

```typescript
Hat
```

A [Hat object](types.md#hat), containing the chosen properties.

_**Example**_:

```typescript
const res = await client.getHat({
  chainId: 10, // optimism
  hatId: BigInt(
    "0x0000000100020001000100000000000000000000000000000000000000000000"
  ),
  props: {
    maxSupply: true, // get the maximum amount of wearers for the hat 
    wearers: { // get the hat's wearers 
      props: {}, // for each wearer, include only its ID (address)
    },
    events: { // get the hat's events
      props: {
        transactionID: true, // for each event, include the transaction ID
      },
      filters: {
        first: 10, // fetch only the latest 10 events
      },
    },
  },
});
```

### <mark style="color:purple;">getHatsByIds</mark>

Get Hats by their IDs.

<pre class="language-typescript"><code class="lang-typescript">const hats = await hatsSubgraphClient.getHatsByIds({
<strong>    chainId,
</strong>    hatIds,
    props,
});
</code></pre>

_**Arguments**_:

```typescript
{
    chainId: number;
    hatIds: bigint[];
    props: HatPropsConfig;
}
```

* `chainId` - ID of the chain to fetch from.
* `hatIds` - IDs of the Hats to fetch.
* `props` - Hat's properties to fetch, including the ones of nested objects. Check the [HatPropsConfig](types.md#hatpropsconfig) type for the available properties and query filters.

_**Response**_:

```typescript
Hat[]
```

An array of [Hat objects](types.md#hat), containing the chosen properties.

_**Example**_:

```typescript
const res = await client.getHatsByIds({
  chainId: 10, // optimism
  hatIds: [
    BigInt("0x0000000100020001000100000000000000000000000000000000000000000000"),
    BigInt("0x0000000100020001000000000000000000000000000000000000000000000000"),
  ],
  props: {
    wearers: { // get each hat's wearers
      props: { 
        currentHats: { // for each wearer, get its hats
          props: {}, // for each hat, include only its ID
        },
      },
    },
  },
});
```
