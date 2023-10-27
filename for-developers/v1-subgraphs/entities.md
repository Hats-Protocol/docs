# 🎩 Hats Protocol Entities

- [`Hat`](#hat)
- [`Wearer`](#wearer)
- [`Tree`](#tree)
- [`HatsEvent`](#hatsevent)
- [`HatCreatedEvent`](#hatcreatedevent)
- [`HatMintedEvent`](#hatmintedevent)
- [`HatBurnedEvent`](#hatburnedevent)
- [`HatStatusChangedEvent`](#hatstatuschangedevent)
- [`HatDetailsChangedEvent`](#hatdetailschangedevent)
- [`HatEligibilityChangedEvent`](#hateligibilitychangedevent)
- [`HatToggleChangedEvent`](#hattogglechangedevent)
- [`HatMutabilityChangedEvent`](#hatmutabilitychangedevent)
- [`HatMaxSupplyChangedEvent`](#hatmaxsupplychangedevent)
- [`HatImageURIChangedEvent`](#hatimageurichangedevent)
- [`TopHatLinkRequestedEvent`](#tophatlinkrequestedevent)
- [`TopHatLinkedEvent`](#tophatlinkedevent)
- [`WearerStandingChangedEvent`](#wearerstandingchangedevent)
- [`ClaimsHatter`](#claimshatter)

## Hat

| Field               | Type             | Description                                     |
| ------------------- | ---------------- | ----------------------------------------------- |
| id                  | ID!              | Unique identifier for the hat                   |
| prettyId            | String!          | Pretty identifier for the hat                   |
| status              | Boolean!         | Status of the hat                               |
| createdAt           | BigInt           | Creation timestamp of the hat                   |
| details             | String!          | Details about the hat                           |
| maxSupply           | BigInt!          | Maximum supply of the hat                       |
| eligibility         | String!          | Eligibility criteria for the hat                |
| toggle              | String!          | Toggle status of the hat                        |
| mutable             | Boolean!         | Mutability status of the hat                    |
| imageUri            | String!          | URI for the hat's image                         |
| levelAtLocalTree    | Int!             | Level of the hat at the local tree              |
| currentSupply       | BigInt!          | Current supply of the hat                       |
| tree                | Tree!            | Associated tree for the hat                     |
| wearers             | [Wearer!]!       | List of wearers for the hat                     |
| admin               | Hat!             | Admin of the hat                                |
| badStandings        | [Wearer!]!       | List of wearers in bad standing                 |
| claimableBy         | [ClaimsHatter!]! | List of hatters who can claim the hat           |
| claimableForBy      | [ClaimsHatter!]! | List of hatters for whom the hat can be claimed |
| linkRequestFromTree | [Tree!]!         | List of trees requesting link to the hat        |
| subHats             | [Hat!]!          | List of sub hats derived from the admin field   |
| linkedTrees         | [Tree!]!         | List of trees linked to the hat                 |
| events              | [HatsEvent!]!    | List of events associated with the hat          |

## Wearer

| Field       | Type               | Description                                    |
| ----------- | ------------------ | ---------------------------------------------- |
| id          | ID!                | Unique identifier for the wearer               |
| currentHats | [Hat!]!            | List of current hats worn by the wearer        |
| mintEvent   | [HatMintedEvent!]! | List of mint events associated with the wearer |
| burnEvent   | [HatBurnedEvent!]! | List of burn events associated with the wearer |

## Tree

| Field               | Type          | Description                             |
| ------------------- | ------------- | --------------------------------------- |
| id                  | ID!           | Unique identifier for the tree          |
| childOfTree         | Tree          | Child tree                              |
| linkedToHat         | Hat           | Hat linked to the tree                  |
| requestedLinkToTree | Tree          | Tree requested for linking              |
| requestedLinkToHat  | Hat           | Hat requested for linking               |
| linkRequestFromTree | [Tree!]!      | List of trees requesting link           |
| hats                | [Hat!]!       | List of hats associated with the tree   |
| parentOfTrees       | [Tree!]!      | List of parent trees                    |
| events              | [HatsEvent!]! | List of events associated with the tree |

## HatsEvent

| Field         | Type    | Description                     |
| ------------- | ------- | ------------------------------- |
| id            | ID!     | Unique identifier for the event |
| tree          | Tree!   | Associated tree for the event   |
| hat           | Hat!    | Associated hat for the event    |
| blockNumber   | Int!    | Block number                    |
| timestamp     | BigInt! | Timestamp of the event          |
| transactionID | Bytes!  | Transaction ID                  |

## HatCreatedEvent

| Field          | Type     | Description                              |
| -------------- | -------- | ---------------------------------------- |
| id             | ID!      | Unique identifier for the event          |
| tree           | Tree!    | Associated tree for the event            |
| hat            | Hat!     | Associated hat for the event             |
| blockNumber    | Int!     | Block number                             |
| timestamp      | BigInt!  | Timestamp of the event                   |
| transactionID  | Bytes!   | Transaction ID                           |
| hatDetails     | String!  | Details of the created hat               |
| hatMaxSupply   | BigInt!  | Maximum supply of the created hat        |
| hatEligibility | String!  | Eligibility criteria for the created hat |
| hatToggle      | String!  | Toggle status of the created hat         |
| hatMutable     | Boolean! | Mutability status of the created hat     |
| hatImageUri    | String!  | URI for the created hat's image          |

## HatMintedEvent

| Field         | Type    | Description                         |
| ------------- | ------- | ----------------------------------- |
| id            | ID!     | Unique identifier for the event     |
| tree          | Tree!   | Associated tree for the event       |
| hat           | Hat!    | Associated hat for the event        |
| blockNumber   | Int!    | Block number                        |
| timestamp     | BigInt! | Timestamp of the event              |
| transactionID | Bytes!  | Transaction ID                      |
| wearer        | Wearer! | Associated wearer of the minted hat |
| operator      | String! | Operator of the minting event       |

## HatBurnedEvent

| Field         | Type    | Description                         |
| ------------- | ------- | ----------------------------------- |
| id            | ID!     | Unique identifier for the event     |
| tree          | Tree!   | Associated tree for the event       |
| hat           | Hat!    | Associated hat for the event        |
| blockNumber   | Int!    | Block number                        |
| timestamp     | BigInt! | Timestamp of the event              |
| transactionID | Bytes!  | Transaction ID                      |
| wearer        | Wearer! | Associated wearer of the burned hat |
| operator      | String! | Operator of the burning event       |

## HatStatusChangedEvent

| Field         | Type     | Description                     |
| ------------- | -------- | ------------------------------- |
| id            | ID!      | Unique identifier for the event |
| tree          | Tree!    | Associated tree for the event   |
| hat           | Hat!     | Associated hat for the event    |
| blockNumber   | Int!     | Block number                    |
| timestamp     | BigInt!  | Timestamp of the event          |
| transactionID | Bytes!   | Transaction ID                  |
| hatNewStatus  | Boolean! | New status of the hat           |

## HatDetailsChangedEvent

| Field         | Type    | Description                     |
| ------------- | ------- | ------------------------------- |
| id            | ID!     | Unique identifier for the event |
| tree          | Tree!   | Associated tree for the event   |
| hat           | Hat!    | Associated hat for the event    |
| blockNumber   | Int!    | Block number                    |
| timestamp     | BigInt! | Timestamp of the event          |
| transactionID | Bytes!  | Transaction ID                  |
| hatNewDetails | String! | New details of the hat          |

## HatEligibilityChangedEvent

| Field             | Type    | Description                     |
| ----------------- | ------- | ------------------------------- |
| id                | ID!     | Unique identifier for the event |
| tree              | Tree!   | Associated tree for the event   |
| hat               | Hat!    | Associated hat for the event    |
| blockNumber       | Int!    | Block number                    |
| timestamp         | BigInt! | Timestamp of the event          |
| transactionID     | Bytes!  | Transaction ID                  |
| hatNewEligibility | String! | New eligibility of the hat      |

## HatToggleChangedEvent

| Field         | Type    | Description                     |
| ------------- | ------- | ------------------------------- |
| id            | ID!     | Unique identifier for the event |
| tree          | Tree!   | Associated tree for the event   |
| hat           | Hat!    | Associated hat for the event    |
| blockNumber   | Int!    | Block number                    |
| timestamp     | BigInt! | Timestamp of the event          |
| transactionID | Bytes!  | Transaction ID                  |
| hatNewToggle  | String! | New toggle status of the hat    |

## HatMutabilityChangedEvent

| Field         | Type    | Description                     |
| ------------- | ------- | ------------------------------- |
| id            | ID!     | Unique identifier for the event |
| tree          | Tree!   | Associated tree for the event   |
| hat           | Hat!    | Associated hat for the event    |
| blockNumber   | Int!    | Block number                    |
| timestamp     | BigInt! | Timestamp of the event          |
| transactionID | Bytes!  | Transaction ID                  |

## HatMaxSupplyChangedEvent

| Field           | Type    | Description                     |
| --------------- | ------- | ------------------------------- |
| id              | ID!     | Unique identifier for the event |
| tree            | Tree!   | Associated tree for the event   |
| hat             | Hat!    | Associated hat for the event    |
| blockNumber     | Int!    | Block number                    |
| timestamp       | BigInt! | Timestamp of the event          |
| transactionID   | Bytes!  | Transaction ID                  |
| hatNewMaxSupply | BigInt! | New maximum supply of the hat   |

## HatImageURIChangedEvent

| Field          | Type    | Description                     |
| -------------- | ------- | ------------------------------- |
| id             | ID!     | Unique identifier for the event |
| tree           | Tree!   | Associated tree for the event   |
| hat            | Hat!    | Associated hat for the event    |
| blockNumber    | Int!    | Block number                    |
| timestamp      | BigInt! | Timestamp of the event          |
| transactionID  | Bytes!  | Transaction ID                  |
| hatNewImageURI | String! | New image URI for the hat       |

## TopHatLinkRequestedEvent

| Field         | Type    | Description                     |
| ------------- | ------- | ------------------------------- |
| id            | ID!     | Unique identifier for the event |
| tree          | Tree!   | Associated tree for the event   |
| hat           | Hat!    | Associated hat for the event    |
| blockNumber   | Int!    | Block number                    |
| timestamp     | BigInt! | Timestamp of the event          |
| transactionID | Bytes!  | Transaction ID                  |
| newAdmin      | Hat!    | New admin for the top hat       |

## TopHatLinkedEvent

| Field         | Type    | Description                      |
| ------------- | ------- | -------------------------------- |
| id            | ID!     | Unique identifier for the event  |
| tree          | Tree!   | Associated tree for the event    |
| hat           | Hat!    | Associated hat for the event     |
| blockNumber   | Int!    | Block number                     |
| timestamp     | BigInt! | Timestamp of the event           |
| transactionID | Bytes!  | Transaction ID                   |
| newAdmin      | Hat!    | New admin for the linked top hat |

## WearerStandingChangedEvent

| Field          | Type     | Description                     |
| -------------- | -------- | ------------------------------- |
| id             | ID!      | Unique identifier for the event |
| tree           | Tree!    | Associated tree for the event   |
| hat            | Hat!     | Associated hat for the event    |
| blockNumber    | Int!     | Block number                    |
| timestamp      | BigInt!  | Timestamp of the event          |
| transactionID  | Bytes!   | Transaction ID                  |
| wearer         | Wearer!  | Associated wearer               |
| wearerStanding | Boolean! | New standing of the wearer      |

## ClaimsHatter

| Field            | Type    | Description                               |
| ---------------- | ------- | ----------------------------------------- |
| id               | ID!     | Unique identifier for the entity          |
| claimableHats    | [Hat!]! | List of hats that can be claimed          |
| claimableForHats | [Hat!]! | List of hats for which claims can be made |
