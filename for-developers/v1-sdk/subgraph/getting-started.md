# Getting Started

### _Install_

yarn:

```bash
yarn add @hatsprotocol/sdk-v1-subgraph
```

npm:

```bash
npm install @hatsprotocol/sdk-v1-subgraph
```

### _HatsSubgraphClient Initialization_

Import and initialize HatsSubgraphClient.

Optionally configure the Subgraph endpoints to use, or use the default ones.&#x20;

```typescript
import { HatsSubgraphClient } from "@hatsprotocol/sdk-v1-subgraph";

const hatsSubgraphClient = new HatsSubgraphClient({
    config
});
```

_**Arguments**_:

```typescript
{ config?: EndpointsConfig }
```

* `config` - Optional subgraph endpoints configuration. If not provided, then the default, un-gated development endpoints will be used. See the `EndpointsConfig` type [here](types.md#endpointsconfig).
