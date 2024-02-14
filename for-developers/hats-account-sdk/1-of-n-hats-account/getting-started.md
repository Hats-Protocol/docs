# Getting Started

### _Install_

yarn:

```bash
yarn add @hatsprotocol/hats-account-sdk viem
```

npm:

```bash
npm install @hatsprotocol/hats-account-sdk viem
```

The SDK uses Viem in order to interact with the various chains and includes it as a peer dependency.

### _HatsAccount1ofNClient Initialization_

Import and initialize _HatsAccount1ofNClient_:

```typescript
import { HatsAccount1ofNClient } from "@hatsprotocol/hats-account-sdk";

const hatsAccount1ofNClient = new HatsAccount1ofNClient({
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
