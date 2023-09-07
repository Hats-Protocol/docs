# Getting Started

### _Install_

yarn:

```bash
yarn add @hatsprotocol/modules-sdk viem@1.2.6
```

npm:

```bash
npm install @hatsprotocol/modules-sdk viem@1.2.6
```

The SDK uses Viem in order to interact with the various chains and includes it as a peer dependency.&#x20;

### _HatsModulesClient Initialization_

Import and initialize HatsModulesClient:

```typescript
import { HatsModulesClient } from "@hatsprotocol/modules-sdk";

const hatsModulesClient = new HatsModulesClient({
    publicClient,
    walletClient,
    registryToken,
});
```

_**Arguments**_:

```typescript
{
    publicClient: PublicClient;
    walletClient: WalletClient;
    registryToken: string
}
```

* `publicClient` - A Viem Public Client, used for onchain read operations.
* `walletClient` - A Viem Wallet Client, used for onchain write operations.&#x20;
* `registryToken` - A GitHub token, used to fetch from the [modules registry,](https://github.com/Hats-Protocol/modules-registry) through GitHub's API.

### _Prepare_

The `prepare` function fetches from the [modules registry](https://github.com/Hats-Protocol/modules-registry). This step is necessary in order to be able to use the client. Additionally, the function accepts an optional `modules` input , in order to support user's caching. If provided, then the client will use the given modules instead of fetching from the registry.

```typescript
await hatsModulesClient.prepare();
```

_**Arguments**_:

```typescript
modules?: Module[]
```

`modules` - Optional array of module objects to use, instead of fetching from the registry.