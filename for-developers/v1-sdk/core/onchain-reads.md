# Onchain Reads

### <mark style="color:purple;">viewHat</mark>

Get a hat's properties.

```typescript
const hat = await hatsClient.viewHat(hatId);
```

_**Arguments**_:

```typescript
hatId: bigint
```

`hatId` - The hat ID. &#x20;

_**Response**_:

```typescript
{
    details: string;
    maxSupply: number;
    supply: number;
    eligibility: Address;
    toggle: Address;
    imageUri: string;
    numChildren: number;
    mutable: boolean;
    active: boolean;
}
```

* `details` - hat's details field.
* `maxSupply` - maximum amount of wearers.
* `supply` - current amount of wearers.
* `eligibility` - hat's eligibility address.
* `toggle` - hat's toggle address.
* `imageUri` - hat's image URI.
* `numChildren` - number of child hats.
* `mutable` - `true` if the hat is mutable, `false` otherwise.
* `active` - `true` if the hat is active, `false` otherwise.

### <mark style="color:purple;">isWearerOfHat</mark>

Check if an address is a wearer of a specific hat.                                                                                 An address is considered a wearer of a hat if the following conditions are met:

* The address owns the hat's token ID (hat ID).
* The hat is active (controlled by the hat's toggle).
* The wearer is eligible for the hat (controlled by the hat's eligibility).

```typescript
const isWearer = await hatsClient.isWearerOfHat({
    wearer,
    hatId,
});
```

_**Arguments**_:

```typescript
{
    wearer: Address;
    hatId: bigint;
}
```

* `wearer` - wearer's address.
* `hatId` - hat's ID.

_**Response**_:

```typescript
boolean
```

`true` if the given address is a wearer of the hat, `false` otherwise.

### <mark style="color:purple;">isAdminOfHat</mark>

Check if an address is an admin of a specific hat.                                                                                An address is an admin of a hat if it wears one of the hat's predecessor hats.

```typescript
const isAdmin = await hatsClient.isAdminOfHat({
    user,
    hatId,
});
```

_**Arguments**_:

```typescript
{
    user: Address;
    hatId: bigint;
}
```

* `user` - address to check whether an admin.
* `hatId` - hat's ID.

_**Response**_:

```typescript
boolean
```

`true` if the given address is an admin of the hat, `false` otherwise.

### <mark style="color:purple;">isActive</mark>

Check if a hat is active.

```typescript
const isActive = await hatsClient.isActive(hatId);
```

_**Arguments**_:

```typescript
hatId: bigint
```

`hatId` - hat's ID.

_**Response**_:

```typescript
boolean
```

`true` if the given hat is active, `false` otherwise.

### <mark style="color:purple;">isInGoodStanding</mark>

Check if a wearer is in good standing for a given hat.

```typescript
const isGoodStanding = await hatsClient.isInGoodStanding({
    wearer,
    hatId,
 });
```

_**Arguments**_:

```typescript
{
    wearer: Address;
    hatId: bigint;
}
```

* `wearer` - address to check whether in good standing.
* `hatId` - hat's ID.

_**Response**_:

```typescript
boolean
```

`true` if the given wearer is in good standing, `false` otherwise.

### <mark style="color:purple;">isEligible</mark>

Check if an address is eligible for a specific hat.

```typescript
const isEligible = await hatsClient.isEligible({
    wearer,
    hatId,
 });
```

_**Arguments**_:

```typescript
{
    wearer: Address;
    hatId: bigint;
}
```

* `wearer` - address to check whether is eligible.
* `hatId` - hat's ID.

_**Response**_:

```typescript
boolean
```

`true` if the given address is eligible for the hat, `false` otherwise.

### <mark style="color:purple;">predictHatId</mark>

Predict the ID of a yet to be created hat.

```typescript
const hatId = await hatsClient.predictHatId(admin);
```

_**Arguments**_:

```typescript
admin: bigint
```

`admin` - parent hat of the would be created one.

_**Response**_:

```typescript
bigint
```

Hat ID of the would be created hat.

### <mark style="color:purple;">getTreesCount</mark>

Get the number of existing trees.

```typescript
const numTrees = await hatsClient.getTreesCount();
```

_**Response**_:

```typescript
number
```

Current number of trees.

### <mark style="color:purple;">getLinkageRequest</mark>

Get the linkage request of a tree.

```typescript
const requestedAdminHat = await hatsClient.getLinkageRequest(topHatDomain);
```

_**Arguments**_:

```typescript
topHatDomain: number
```

`topHatDomain` - the tree domain. The tree domain is the first four bytes of the tophat ID.

_**Response**_:

```typescript
bigint
```

If request exists, returns the requested new admin hat ID. If not, returns zero.

### <mark style="color:purple;">getLinkedTreeAdmin</mark>

Get the admin of a linked tree (the hat which the tophat is linked to).

```typescript
const adminHat = await hatsClient.getLinkedTreeAdmin(topHatDomain);
```

_**Arguments**_:

```typescript
topHatDomain: number
```

`topHatDomain` - the tree domain. The tree domain is the first four bytes of the tophat ID.

_**Response**_:

```typescript
bigint
```

If tree is linked, returns the admin hat ID of the linked tree. If not, returns zero.

### <mark style="color:purple;">getHatLevel</mark>

Get a hat's level. If the tree is linked, level is calculated in the global tree (comprised of all linked trees).

```typescript
const level = await hatsClient.getHatLevel(hatId);
```

_**Arguments**_:

```typescript
hatId: bigint
```

`hatId` - hat's ID.

_**Response**_:

```typescript
number
```

The hat's level in the global tree.

### <mark style="color:purple;">getLocalHatLevel</mark>

Get a hat's level in its local tree (without considering linked trees).                                                          &#x20;

```typescript
const level = await hatsClient.getLocalHatLevel(hatId);
```

_**Arguments**_:

```typescript
hatId: bigint
```

`hatId` - hat's ID.

_**Response**_:

```typescript
number
```

The hat's local level.

### <mark style="color:purple;">getTopHatDomain</mark>

Get a hat's tree domain.                          &#x20;

```typescript
const domain = await hatsClient.getTopHatDomain(hatId);
```

_**Arguments**_:

```typescript
hatId: bigint
```

`hatId` - hat's ID.

_**Response**_:

```typescript
number
```

The tree domain of the hat. The tree domain is the first four bytes of the tophat ID.

### <mark style="color:purple;">getTippyTopHatDomain</mark>

Get the tree domain of the global's tree tophat (tippy top hat), which the provided tree is included in.

```typescript
const domain = await hatsClient.getTippyTopHatDomain(topHatDomain);
```

_**Arguments**_:

```typescript
topHatDomain: number
```

`topHatDomain` - The tree domain. The tree domain is the first four bytes of its tophat ID.

_**Response**_:

```typescript
number
```

The tree domain of the tippy top hat.

### <mark style="color:purple;">getAdmin</mark>

Get the direct admin of a hat.&#x20;

```typescript
const admin = await hatsClient.getAdmin(hatId);
```

_**Arguments**_:

```typescript
hatId: bigint
```

`hatId` - hat's ID.

_**Response**_:

```typescript
bigint
```

The admin's hat ID. If the provided hat is an unlinked tophat, then this top hat ID is returned, as it is the admin of itself. Otherwise, the hat's parent hat ID is returned.

### <mark style="color:purple;">getChildrenHats</mark>

Get the children hats of a hat.

```typescript
const children = await hatsClient.getChildrenHats(hatId);
```

_**Arguments**_:

```typescript
hatId: bigint
```

`hatId` - hat's ID.

_**Response**_:

```typescript
bigint[]
```

The hat's children IDs.
