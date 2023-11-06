# Hat & Tree ID Utilities

Following are utility functions to handle various hat & tree ID formats. More information about hat IDs can be found [here](../../hats-protocol-overview/hat-ids.md).

### <mark style="color:purple;">hatIdDecimalToHex</mark>

Convert a hat ID from decimal to hex.

```typescript
import { hatIdDecimalToHex } from "@hatsprotocol/sdk-v1-core";

const hatIdHex = hatIdDecimalToHex(hatId);
```

_**Arguments**_:

```typescript
hatId: bigint
```

`hatId` - Hat ID in decimal format.

_**Response**_:

```typescript
string
```

Hat ID in a hex format.

### <mark style="color:purple;">hatIdHexToDecimal</mark>

Convert a hat ID from hex to decimal.

```typescript
import { hatIdHexToDecimal } from "@hatsprotocol/sdk-v1-core";

const hatIdDecimal = hatIdHexToDecimal(hatId);
```

_**Arguments**_:

```typescript
hatId: string
```

`hatId` - Hat ID in hex format.

_**Response**_:

```typescript
bigint
```

Hat ID in a decimal format.

### <mark style="color:purple;">treeIdDecimalToHex</mark>

Convert a tree ID from decimal to hex. A tree ID is the first 4 bytes in a hat ID.

```typescript
import { treeIdDecimalToHex } from "@hatsprotocol/sdk-v1-core";

const treeIdHex = treeIdDecimalToHex(treeId);
```

_**Arguments**_:

```typescript
treeId: number
```

`treeId` - Tree ID in decimal format.&#x20;

_**Response**_:

```typescript
string
```

Tree ID in a hex format.

### <mark style="color:purple;">treeIdHexToDecimal</mark>

Convert a tree ID from hex to decimal. A tree ID is the first 4 bytes in a hat ID.

```typescript
import { treeIdHexToDecimal } from "@hatsprotocol/sdk-v1-core";

const treeIdDecimal = treeIdHexToDecimal(treeId);
```

_**Arguments**_:

```typescript
treeId: string
```

`treeId` - Tree ID in hex format.&#x20;

_**Response**_:

```typescript
number
```

Tree ID in a decimal format.

### <mark style="color:purple;">treeIdToTopHatId</mark>

Convert a tree ID to its top-hat ID. A tree ID is the first 4 bytes in a hat ID.

```typescript
import { treeIdToTopHatId } from "@hatsprotocol/sdk-v1-core";

const tophatId = treeIdToTopHatId(treeId);
```

_**Arguments**_:

```typescript
treeId: number
```

`treeId` - Tree ID in decimal format.&#x20;

_**Response**_:

```typescript
bigint
```

Top-hat ID in decimal format.

### <mark style="color:purple;">hatIdToTreeId</mark>

Convert a hat ID to its tree ID. A tree ID is the first 4 bytes in a hat ID.

```typescript
import { hatIdToTreeId } from "@hatsprotocol/sdk-v1-core";

const treeId = hatIdToTreeId(hatId);
```

_**Arguments**_:

```typescript
hatId: bigint
```

`hatId` - Hat ID in decimal format.&#x20;

_**Response**_:

```typescript
number
```

Tree ID of the hat, in a decimal format.

### <mark style="color:purple;">hatIdDecimalToIp</mark>

The IP format may be used as a "pretty" hat ID format for presenting.&#x20;

For example, a hat with a hex ID of:\
`0x00000001000a0002000000000000000000000000000000000000000000000000`  will have an IP format of 1.10.2 - Each level is separated by a dot and presented as a decimal number, excluding zeros.&#x20;

```typescript
import { hatIdDecimalToIp } from "@hatsprotocol/sdk-v1-core";

const hatIdIp = hatIdDecimalToIp(hatId);
```

_**Arguments**_:

```typescript
hatId: bigint
```

`hatId` - Hat ID in decimal format.&#x20;

_**Response**_:

```typescript
string
```

Hat ID in IP format.
