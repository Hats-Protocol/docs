# Types

### <mark style="color:purple;">Hat</mark>

```typescript
interface Hat {
  id: string; // Hat ID
  prettyId?: string; // pretty ID format
  status?: boolean; // 'true' if active, 'false' otherwise
  createdAt?: string; // timestamp of hat creation
  details?: string; // Hat's details field
  maxSupply?: string; // max amount of wearers
  eligibility?: `0x${string}`; // eligibility address
  toggle?: `0x${string}`; // toggle address
  mutable?: boolean; // 'true' if mutable, 'false' otherwise
  imageUri?: string; // Hat's image URI
  levelAtLocalTree?: number; // Hat's level at its local tree (not including linked trees)
  currentSupply?: string; // current amount of hat wearers
  tree?: Tree; // Tree which contains the Hat
  wearers?: Wearer[]; // Hat's Wearers
  badStandings?: Wearer[]; // Hat's Wearers in bad standing
  admin?: Hat; // Hat's admin Hat
  subHats?: Hat[]; // Hat's children Hats
  linkRequestFromTree?: Tree[];  // Link requests from Trees
  linkedTrees?: Tree[]; // Trees linked to the Hat
  claimableBy?: ClaimsHatter[]; // Claims Hatters that the Hat is made claimable by
  claimableForBy?: ClaimsHatter[]; // Claims Hatters that the Hat is made claimable for by
  events?: HatsEvent[]; // Hat's events
}
```

### <mark style="color:purple;">HatConfig</mark>

Query configuration for a [Hat](types.md#hat)'s properties.&#x20;

The Hat's ID property is required and thus is not included in the config. The rest of the properties are optional. &#x20;

To choose Scalar properties (non-object), include their key with a value of `true`. To choose an Object property, include its key with a value compatible with the object's config.

```typescript
interface HatConfig {
  prettyId?: boolean;
  status?: boolean;
  createdAt?: boolean;
  details?: boolean;
  maxSupply?: boolean;
  eligibility?: boolean;
  toggle?: boolean;
  mutable?: boolean;
  imageUri?: boolean;
  levelAtLocalTree?: boolean;
  currentSupply?: boolean;
  tree?: TreeConfig;
  wearers?: WearerConfig;
  badStandings?: WearerConfig;
  admin?: HatConfig;
  subHats?: HatConfig;
  linkRequestFromTree?: TreeConfig;
  linkedTrees?: TreeConfig;
  claimableBy?: ClaimsHatterConfig;
  claimableForBy?: ClaimsHatterConfig;
  events?: HatsEventConfig;
}
```

### <mark style="color:purple;">Wearer</mark>

```typescript
interface Wearer {
  id: string; // Wearer's address
  currentHats?: Hat[]; // Wearer's current Hats
  mintEvent?: HatsEvent[]; // Hat mint events for the Wearer
  burnEvent?: HatsEvent[]; // Hat burn events for the Wearer
}
```

### <mark style="color:purple;">WearerConfig</mark>

Query configuration for a Wearer's properties.&#x20;

The Wearer's ID property is required and thus is not included in the config. The rest of the properties are optional. &#x20;

To choose Scalar properties (non-object), include their key with a value of `true`. To choose an Object property, include its key with a value compatible with the object's config.

```typescript
interface WearerConfig {
  currentHats?: HatConfig;
  mintEvent?: HatsEventConfig;
  burnEvent?: HatsEventConfig;
}
```

### <mark style="color:purple;">Tree</mark>

```typescript
interface Tree {
  id: number; // Tree ID (Tree's top-hat domain - first 4 bytes of the top-hat ID)
  hats?: Hat[]; // Tree's Hats
  childOfTree?: Tree; // if linked, the Tree which this Tree is linked to
  parentOfTrees?: Tree[]; // Trees which are linked to this Tree
  linkedToHat?: Hat; // if linked, the Hat which this Tree is linked to
  linkRequestFromTree?: Tree[]; // Trees with a linkage request to this Tree
  requestedLinkToTree?: Tree; // Tree which this Tree has a linkage request to
  requestedLinkToHat?: Hat; // Hat which this Tree has a linkage request to
  events?: HatsEvent[]; // Tree's events
}
```

### <mark style="color:purple;">TreeConfig</mark>

Query configuration for a Tree's properties.&#x20;

The Tree's ID property is required and thus is not included in the config. The rest of the properties are optional. &#x20;

To choose Scalar properties (non-object), include their key with a value of `true`. To choose an Object property, include its key with a value compatible with the object's config.

```typescript
interface TreeConfig {
  hats?: HatConfig;
  childOfTree?: TreeConfig;
  parentOfTrees?: TreeConfig;
  linkedToHat?: HatConfig;
  linkRequestFromTree?: TreeConfig;
  requestedLinkToTree?: TreeConfig;
  requestedLinkToHat?: HatConfig;
  events?: HatsEventConfig;
}
```

### <mark style="color:purple;">HatsEvent</mark>

```typescript
interface HatsEvent {
  id: string; // Event's ID
  timestamp?: bigint; // Event's timestamp
  blockNumber?: number; // Event's blocke number
  transactionID?: string; // transaction ID which the Event was emitted in
  hat?: Hat; // Hat that relates to the Event
  tree?: Tree; // Tree that relates to the Event
}
```

### <mark style="color:purple;">HatsEventConfig</mark>

Query configuration for a HatsEvent's properties.&#x20;

The HatsEvent's ID property is required and thus is not included in the config. The rest of the properties are optional. &#x20;

To choose Scalar properties (non-object), include their key with a value of `true`. To choose an Object property, include its key with a value compatible with the object's config.

```typescript
interface HatsEventConfig {
  timestamp?: boolean;
  blockNumber?: boolean;
  transactionID?: boolean;
  hat?: HatConfig;
  tree?: TreeConfig;
}
```

### <mark style="color:purple;">ClaimsHatter</mark>

```typescript
interface ClaimsHatter {
  id: string; // ClaimsHatter's ID
  claimableHats?: Hat[]; // Hats made claimable by this Hatter
  claimableForHats?: Hat[]; // Hats made 'claimable for' by this Hatter 
}
```

### <mark style="color:purple;">ClaimsHatterConfig</mark>

Query configuration for a ClaimsHatter's properties.&#x20;

The ClaimsHatter's ID property is required and thus is not included in the config. The rest of the properties are optional. &#x20;

To choose Scalar properties (non-object), include their key with a value of `true`. To choose an Object property, include its key with a value compatible with the object's config.

```typescript
interface ClaimsHatterConfig {
  claimableHats?: HatConfig;
  claimableForHats?: HatConfig;
}
```

### <mark style="color:purple;">Filters</mark>

Optional filters to include in the GraphQL query:

* `filter` - For each property that returns multiple objects, optionally configure the amount of objects to fetch. If not included, the amount of fetched objects will be the endpoint's default amount. The properties are grouped according to the objects they are included in (Hat, Wearer, Tree...).

```typescript
interface Filters {
  first?: { // "first" filter 
    hat?: { // Hat properties
      wearers?: number; 
      badStandings?: number;
      subHats?: number;
      linkRequestFromTree?: number;
      linkedTrees?: number;
      claimableBy?: number;
      claimableForBy?: number;
      events?: number;
    };
    wearer?: { // Wearer properties
      currentHats?: number;
      mintEvent?: number;
      burnEvent?: number;
    };
    tree?: { // Tree properties
      hats?: number;
      parentOfTrees?: number;
      linkRequestFromTree?: number;
      events?: number;
    };
    claimsHatter?: { //g ClaimsHatter properties
      claimableHats?: number;
      claimableForHats?: number;
    };
  };
}
```
