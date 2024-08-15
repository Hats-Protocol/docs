# Getting Started

## _Overview_

The package supports storing and reading a hat's metadata from IPFS.&#x20;

Data is stored in a JSON format, and follows a custom schema which is passed by the user at the client's initialization. By using a schema for the data, we're able to validate that the data is compatible with an expected format.&#x20;

The package uses the [Zod](https://zod.dev/) library for the schema definition and validation. The schema is also used for type inference, providing type-safety for its users.

## _Install_

yarn:

```bash
yarn add @hatsprotocol/details-sdk zod
```

npm:

```bash
npm install @hatsprotocol/details-sdk zod
```

## _HatsDetailsClient Initialization_

A HatsDetailsClient instance is initialized with an IPFS provider (currently only [Pinata](https://www.pinata.cloud/) is supported) and a schema, defined with the [Zod](https://zod.dev/) library.

### Choose which schema to use&#x20;

#### Option 1 - use the default schema

If the client is initialized without a custom schema, then the default schema will be used. This schema is compatible with the [Hats App](https://app.hatsprotocol.xyz/), meaning that this app will properly display hats with this type of details.

```typescript
import { HatsDetailsClient } from "@hatsprotocol/details-sdk";

let hatsDetailsClient: HatsDetailsClient;
hatsDetailsClient = new HatsDetailsClient({
      provider: "pinata",
      pinata: {
        pinningKey: process.env.PINATA_JWT as string,
      },
});
```

Here's the default schema:

```typescript
z.object({
  type: z.literal("1.0"),
  data: z.object({
    name: z.string(),
    description: z.string().optional(),
    responsabilities: z
      .array(
        z.object({
          label: z.string(),
          description: z.string().optional(),
          link: z.string().optional(),
          imageUrl: z.string().optional(),
        })
      )
      .optional(),
    authorities: z
      .array(
        z.object({
          label: z.string(),
          description: z.string().optional(),
          link: z.string().optional(),
          imageUrl: z.string().optional(),
          gate: z.string().optional(),
        })
      )
      .optional(),
  }),
});
```

The corresponding type for this schema is:

```typescript
{
    type: "1.0";
    data: {
        name: string;
        description?: string | undefined;
        responsabilities?: {
            label: string;
            description?: string | undefined;
            link?: string | undefined;
            imageUrl?: string | undefined;
        }[] | undefined;
        authorities?: {
            label: string;
            description?: string | undefined;
            link?: string | undefined;
            imageUrl?: string | undefined;
            gate?: string | undefined;
        }[] | undefined;
    };
}
```

#### Option 2 - use a custom schema

You can define a custom schema for the client, for example:

```typescript
import * as z from "zod";

const schema = z.object({
  name: z.string(),
  description: z.string(),
});

let hatsDetailsClient: HatsDetailsClient<typeof schema>;
hatsDetailsClient = new HatsDetailsClient({
      schema,
      provider: "pinata",
      pinata: {
        pinningKey: process.env.PINATA_JWT as string,
      },
});
```

### Set up the Pinata provider

The client is initialized with an IPFS provider that will be used for storing and reading to/from IPFS. Currently, Pinata is the only supported provider and is initialized with the following properties:

```typescript
{
   pinningKey: string;
   gateway?: string;
   gatewayKey?: string;
}
```

* `pinningKey` - this as a JWT that's used for pinning data, and is required at the client's initialization.
* `gateway` - a dedicated gateway URL, that's provided by Pinata and is used to read IPFS data. This property is optional. If not, provided then the default gateway that's provided by [https://ipfs.io](https://ipfs.io/) will be used.
* `gatewayKey` - optional key that is used to secure dedicated Pinata gateways. If provided along with a gateway, then the key will be used for fetching data.
