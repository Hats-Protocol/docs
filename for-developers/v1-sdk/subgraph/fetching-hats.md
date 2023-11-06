# Fetching Hats

### <mark style="color:purple;">getHat</mark>

Get a Hat by its ID.

```typescript
const hat = await hatsSubgraphClient.getHat({
    chainId,
    hatId,
    props,
    filters,
});
```

_**Arguments**_:

```typescript
{
    chainId: number;
    hatId: bigint;
    props: HatConfig;
    filters?: Filters;
}
```

* `chainId` - ID of the chain to fetch from.
* `hatId` - ID of the Hat to fetch.
* `props` - Hat's properties to fetch, including the ones of nested objects. Check the [HatConfig](types.md#hatconfig) type for the available properties.
* `filters` - Optional filters to include in the GraphQL query. Check the [Filters](types.md#filters) type for the available filters.

_**Response**_:

```typescript
Hat
```

A [Hat object](types.md#hat), containing the chosen properties.

### <mark style="color:purple;">getHatsByIds</mark>

Get Hats by their IDs.

<pre class="language-typescript"><code class="lang-typescript">const hats = await hatsSubgraphClient.getHatsByIds({
<strong>    chainId,
</strong>    hatIds,
    props,
    filters,
});
</code></pre>

_**Arguments**_:

```typescript
{
    chainId: number;
    hatIds: bigint[];
    props: HatConfig;
    filters?: Filters;
}
```

* `chainId` - ID of the chain to fetch from.
* `hatIds` - IDs of the Hats to fetch.
* `props` - Hat's properties to fetch, including the ones of nested objects. Check the [HatConfig](types.md#hatconfig) type for the available properties.
* `filters` - Optional filters to include in the GraphQL query. Check the [Filters](types.md#filters) type for the available filters.

_**Response**_:

```typescript
Hat[]
```

An array of [Hat objects](types.md#hat), containing the chosen properties.
