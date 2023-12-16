# Getting Started

### _Install_

yarn:

```bash
yarn add @hatsprotocol/hsg-sdk viem
```

npm:

```bash
npm install @hatsprotocol/hsg-sdk viem
```

The SDK uses Viem in order to interact with the various chains and includes it as a peer dependency.

### _HatsSignerGateClient Initialization_

Import and initialize _HatsSignerGateClient_:

```typescript
import { HatsSignerGateClient } from "@hatsprotocol/hsg-sdk";

const hatsSignerGateClient = new HatsSignerGateClient({
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
