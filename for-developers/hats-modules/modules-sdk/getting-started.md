# Getting Started

### _Install_

yarn:

```bash
yarn add @hatsprotocol/modules-sdk viem
```

npm:

```bash
npm install @hatsprotocol/modules-sdk viem
```

The SDK uses Viem in order to interact with the various chains and includes it as a peer dependency.

### _HatsModulesClient Initialization_

Import and initialize HatsModulesClient:

```typescript
import { HatsModulesClient } from "@hatsprotocol/modules-sdk";

const hatsModulesClient = new HatsModulesClient({
    publicClient,
    walletClient,
});
```

_**Arguments**_:

```typescript
{
    publicClient: PublicClient;
    walletClient: WalletClient;
}
```

* `publicClient` - A Viem Public Client, used for onchain read operations.
* `walletClient` - A Viem Wallet Client, used for onchain write operations.&#x20;

### _Prepare_

The `prepare` function fetches from the [modules registry](https://github.com/Hats-Protocol/modules-registry). This step is necessary in order to be able to use the client. Additionally, the function accepts an optional `registry` input , in order to support user's caching. If provided, then the client will use the given modules instead of fetching from the registry.

```typescript
await hatsModulesClient.prepare();
```

_**Arguments**_:

```typescript
registry?: Registry
```

`registry` - Optional [registry object](types.md#registry) to use, instead of fetching from the current registry.
