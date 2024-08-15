# Usage

Once initialized, the HatsDetailsClient can be used for reading and storing data from/to IPFS, in a predetermined format.&#x20;

## Store

Use the the following function in order to store/pin data to IPFS.&#x20;

The data is expected to be compatible with the provided schema, otherwise an error will be thrown. If data was successfully pinned, its CID (content identifier). This can then be used for reading the data back from IPFS.

```typescript
const cid = await hatsDetailsClient.pin({
    type: "1.0",
    data: {
        name: "Hat",
        description: "This is a hat",
    },
});
```

## Read

Read data from IPFS.

```typescript
const data = await hatsDetailsClientDefaultSchema.get(
    "QmcSopxmw5rMEEEU8NmGGQ2mbHJ293CGEiQ4r4w4jEECVy"
);
```

The returned data has the following type:

```typescript
{
    parsedData: z.infer<T> | null;
    rawData: unknown | null;
    error: { message: string } | null;
}
```

* If data was successfully fetched and is compatible with the client's schema, then the parsed data will be in the `parsedData` field, while the `rawData` and `error` fields will be `null`.
* If data was successfully fetched but is not compatible with the client's schema, then the data will be in the `rawData` field, while the `data` and `error` fields will be `null`.
* If an error occurred, then the `data` and `rawData` fields will be `null`, and the `error` field will contain an object with a `message` field.

