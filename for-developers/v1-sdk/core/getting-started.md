# Getting Started

### _Install_

yarn:

```bash
yarn add @hatsprotocol/sdk-v1-core viem
```

npm:

```bash
npm install @hatsprotocol/sdk-v1-core viem
```

The SDK uses Viem in order to interact with the various chains and includes it as a peer dependency.

### _HatsClient Initialization_

Import and initialize HatsClient:

```typescript
import { HatsClient } from "@hatsprotocol/sdk-v1-core";

const hatsClient = new HatsClient({
    chainId,
    publicClient,
    walletClient,
});
```

_**Arguments**_:

```typescript
{
    chainId: number;
    publicClient: PublicClient;
    walletClient?: WalletClient;
}
```

* `chainId` - Client's chain ID. The client is initialized to work with one specific chain.
* `publicClient` - A Viem Public Client, used for onchain read operations.
* `walletClient` (Optional) - A Viem Wallet Client, used for onchain write operations. If not provided, then this Hats Client will support only read operations.
