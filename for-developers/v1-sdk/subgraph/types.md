# Types

## Hat Types

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

### <mark style="color:purple;">HatPropsConfig</mark>

Query configuration for a [Hat](types.md#hat)'s properties.&#x20;

The Hat's ID property is required and thus is not included in the config. The rest of the properties are optional. &#x20;

* To choose Scalar properties (non-object), include their key with a value of `true`.&#x20;
* To choose an Object property, include its key with a value compatible with the object's config type:
  * For single-object properties (e.g. `tree`), the config type includes the object's available properties without filters.
  * For multi-object properties (e.g. `wearers`), the config type includes both the object's available properties and optional filters (currently supports only the 'first' filter).

```typescript
interface HatPropsConfig {
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
  tree?: TreePropsConfig;
  wearers?: WearersConfig;
  badStandings?: WearersConfig;
  admin?: HatPropsConfig;
  subHats?: HatsConfig;
  linkRequestFromTree?: TreesConfig;
  linkedTrees?: TreesConfig;
  claimableBy?: ClaimsHattersConfig;
  claimableForBy?: ClaimsHattersConfig;
  events?: HatsEventsConfig;
}
```

### <mark style="color:purple;">HatsConfig</mark>

Query configuration for a multi [Hat](types.md#hat)s property, i.e. a property that returns multiple Hats.

```typescript
interface HatsConfig {
  props: HatPropsConfig; // properties to include in each hat
  filters?: { // filters to apply on the property query
    first?: number; // fetch only the 'first' amount of hats
  };
}
```

## Wearer Types

### <mark style="color:purple;">Wearer</mark>

```typescript
interface Wearer {
  id: string; // Wearer's address
  currentHats?: Hat[]; // Wearer's current Hats
  mintEvent?: HatsEvent[]; // Hat mint events for the Wearer
  burnEvent?: HatsEvent[]; // Hat burn events for the Wearer
}
```

### <mark style="color:purple;">WearerPropsConfig</mark>

Query configuration for a [Wearer](types.md#wearer)'s properties.&#x20;

The Wearer's ID property is required and thus is not included in the config. The rest of the properties are optional. &#x20;

* To choose Scalar properties (non-object), include their key with a value of `true`.&#x20;
* To choose an Object property, include its key with a value compatible with the object's config type:
  * For single-object properties (e.g. the `tree` property of a Hat), the config type includes the object's available properties.
  * For multi-object properties (e.g. `currentHats`), the config type includes both the object's available properties and optional filters (currently supports only the 'first' filter).

```typescript
interface WearerPropsConfig {
 currentHats?: HatsConfig;
  mintEvent?: HatsEventsConfig;
  burnEvent?: HatsEventsConfig;
}
```

### <mark style="color:purple;">WearersConfig</mark>

Query configuration for a multi [Wearer](types.md#wearer)s property, i.e. a property that returns multiple Wearers.

```typescript
interface WearerPropsConfig {
  props: WearerPropsConfig; // properties to include in each wearer
  filters?: { // filters to apply on the property query
    first?: number; // fetch only the 'first' amount of wearers
  };
}
```

## Tree Types

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

### <mark style="color:purple;">TreePropsConfig</mark>

Query configuration for a [Tree](types.md#tree)'s properties.&#x20;

The Tree's ID property is required and thus is not included in the config. The rest of the properties are optional. &#x20;

* To choose Scalar properties (non-object), include their key with a value of `true`.&#x20;
* To choose an Object property, include its key with a value compatible with the object's config type:
  * For single-object properties (e.g. `childOfTree`), the config type includes the object's available properties.
  * For multi-object properties (e.g. `hats`), the config type includes both the object's available properties and optional filters (currently supports only the 'first' filter).

```typescript
interface TreePropsConfig {
  hats?: HatsConfig;
  childOfTree?: TreePropsConfig;
  parentOfTrees?: TreesConfig;
  linkedToHat?: HatPropsConfig;
  linkRequestFromTree?: TreesConfig;
  requestedLinkToTree?: TreePropsConfig;
  requestedLinkToHat?: HatPropsConfig;
  events?: HatsEventsConfig;
}
```

### <mark style="color:purple;">TreesConfig</mark>

Query configuration for a multi [Tree](types.md#tree)s property, i.e. a property that returns multiple Trees.

```typescript
interface TreePropsConfig {
  props: TreePropsConfig; // properties to include in each tree
  filters?: { // filters to apply on the property query
    first?: number; // fetch only the 'first' amount of trees
  };
}
```

## Event Types

### <mark style="color:purple;">HatsEventBase</mark>

Base type, which contains the common properties of Hats Events, and which is then extended by each specific event.

```typescript
interface HatsEventBase {
  id: string; // Event's ID
  timestamp?: bigint; // Event's timestamp
  blockNumber?: number; // Event's block number
  transactionID?: string; // transaction ID which the Event was emitted in
  hat?: Hat; // Hat that relates to the Event
  tree?: Tree; // Tree that relates to the Event
}
```

### <mark style="color:purple;">HatsEventPropsConfig</mark>

Query configuration for the basic properties of a Hats Event.

The HatsEvent's ID property is required and thus is not included in the config. The rest of the properties are optional. &#x20;

To choose Scalar properties (non-object), include their key with a value of `true`. To choose an Object property, include its key with a value compatible with the object's config.

```typescript
interface HatsEventConfig {
  timestamp?: boolean;
  blockNumber?: boolean;
  transactionID?: boolean;
  hat?: HatPropsConfig;
  tree?: HatPropsConfig;
}
```



Following are the various Hats Events, emitted from Hats-Protocol in response to various actions.

Fetched events will include the event's [base properties](types.md#hatseventbase), as well as the additional properties that are included in each specific event, according to its type.

### <mark style="color:purple;">HatCreatedEvent</mark>

```typescript
interface HatCreatedEvent extends HatsEventBase {
  __typename: "HatCreatedEvent";
  hatDetails: string;
  hatMaxSupply: string;
  hatEligibility: string;
  hatToggle: string;
  hatMutable: boolean;
  hatImageUri: string;
}
```

### <mark style="color:purple;">HatMintedEvent</mark>

```typescript
interface HatMintedEvent extends HatsEventBase {
  __typename: "HatMintedEvent";
  wearer: {
    id: string;
  };
  operator: string;
}
```

### <mark style="color:purple;">HatBurnedEvent</mark>

```typescript
interface HatBurnedEvent extends HatsEventBase {
  __typename: "HatBurnedEvent";
  wearer: {
    id: string;
  };
  operator: string;
}
```

### <mark style="color:purple;">HatMutabilityChangedEvent</mark>

```typescript
interface HatMutabilityChangedEvent extends HatsEventBase {
  __typename: "HatMutabilityChangedEvent";
}
```

### <mark style="color:purple;">HatStatusChangedEvent</mark>

```typescript
interface HatStatusChangedEvent extends HatsEventBase {
  __typename: "HatStatusChangedEvent";
  hatNewStatus: boolean;
}
```

### <mark style="color:purple;">HatDetailsChangedEvent</mark>

```typescript
interface HatDetailsChangedEvent extends HatsEventBase {
  __typename: "HatDetailsChangedEvent";
  hatNewDetails: string;
}
```

### <mark style="color:purple;">HatEligibilityChangedEvent</mark>

```typescript
interface HatEligibilityChangedEvent extends HatsEventBase {
  __typename: "HatEligibilityChangedEvent";
  hatNewEligibility: string;
}
```

### <mark style="color:purple;">HatToggleChangedEvent</mark>

```typescript
interface HatToggleChangedEvent extends HatsEventBase {
  __typename: "HatToggleChangedEvent";
  hatNewToggle: string;
}
```

### <mark style="color:purple;">HatMaxSupplyChangedEvent</mark>

```typescript
interface HatMaxSupplyChangedEvent extends HatsEventBase {
  __typename: "HatMaxSupplyChangedEvent";
  hatNewMaxSupply: string;
}
```

### <mark style="color:purple;">HatImageURIChangedEvent</mark>

```typescript
interface HatImageURIChangedEvent extends HatsEventBase {
  __typename: "HatImageURIChangedEvent";
  hatNewImageURI: string;
}
```

### <mark style="color:purple;">TopHatLinkRequestedEvent</mark>

```typescript
interface TopHatLinkRequestedEvent extends HatsEventBase {
  __typename: "TopHatLinkRequestedEvent";
  newAdmin: string;
}
```

### <mark style="color:purple;">TopHatLinkedEvent</mark>

```typescript
interface TopHatLinkedEvent extends HatsEventBase {
  __typename: "TopHatLinkedEvent";
  newAdmin: string;
}
```

### <mark style="color:purple;">WearerStandingChangedEvent</mark>

```typescript
interface WearerStandingChangedEvent extends HatsEventBase {
  __typename: "WearerStandingChangedEvent";
  wearer: {
    id: string;
  };
  wearerStanding: boolean;
}
```

### <mark style="color:purple;">HatsEvent</mark>

```typescript
type HatsEvent =
  | HatCreatedEvent
  | HatMintedEvent
  | HatBurnedEvent
  | HatMutabilityChangedEvent
  | HatStatusChangedEvent
  | HatDetailsChangedEvent
  | HatEligibilityChangedEvent
  | HatToggleChangedEvent
  | HatMaxSupplyChangedEvent
  | HatImageURIChangedEvent
  | TopHatLinkRequestedEvent
  | TopHatLinkedEvent
  | WearerStandingChangedEvent;
```

## Claims Hatter Types

### <mark style="color:purple;">ClaimsHatter</mark>

```typescript
interface ClaimsHatter {
  id: string; // ClaimsHatter's ID
  claimableHats?: Hat[]; // Hats made claimable by this Hatter
  claimableForHats?: Hat[]; // Hats made 'claimable for' by this Hatter 
}
```

### <mark style="color:purple;">ClaimsHatterPropsConfig</mark>

Query configuration for a ClaimsHatter's properties.&#x20;

The ClaimsHatter's ID property is required and thus is not included in the config. The rest of the properties are optional. &#x20;

```typescript
interface ClaimsHatterPropsConfig {
  claimableHats?: HatsConfig;
  claimableForHats?: HatsConfig;
}
```

### <mark style="color:purple;">ClaimsHattersConfig</mark>

Query configuration for a multi [ClaimsHatter](types.md#claimshatter)s property, e.g. a property that returns multiple Claims Hatters.

```typescript
interface ClaimsHattersConfig {
  props: ClaimsHatterPropsConfig; // properties to include in each claims hatter
  filters?: { // filters to apply on the property query
    first?: number; // fetch only the 'first' amount of hatters
  };
}
```

## More

### <mark style="color:purple;">EndpointsConfig</mark>

Subgraph endpoints configuration, optionally provided at the client's creation.

```typescript
interface EndpointsConfig {
  [chainId: number]: { endpoint: string };
}
```
