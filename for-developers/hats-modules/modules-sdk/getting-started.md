# Getting Started

### _Install_

yarn:

```bash
yarn add @hatsprotocol/modules-sdk viem@1.9.5
```

npm:

```bash
npm install @hatsprotocol/modules-sdk viem@1.9.5
```

The SDK uses Viem in order to interact with the various chains and includes it as a peer dependency.

{% hint style="info" %}
It is required to use the exact Viem version that the SDK is using internally (v1.9.5). Otherwise, Viem's Typescript types might be incompatible between the SDK and its user. Check their documentation [here](https://viem.sh/docs/typescript.html#typescript) to learn more.&#x20;

One possible approach is having a separate Viem instance, using package aliasing.
{% endhint %}

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

The `prepare` function fetches from the [modules registry](https://github.com/Hats-Protocol/modules-registry). This step is necessary in order to be able to use the client. Additionally, the function accepts an optional `modules` input , in order to support user's caching. If provided, then the client will use the given modules instead of fetching from the registry.

```typescript
await hatsModulesClient.prepare();
```

_**Arguments**_:

```typescript
modules?: Module[]
```

`modules` - Optional array of module objects to use, instead of fetching from the registry.
