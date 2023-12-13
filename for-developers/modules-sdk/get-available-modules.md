# Get Available Modules

The following functions are used in order to get available modules, as exist in the [Modules Registry](../hats-modules/building-hats-modules/modules-registry.md).

Modules are represented as Module objects, with the following type:

```typescript
{
  name: string; // module's name
  deprecated?: boolean; // if 'true', indicates that new instances of this module should not be created
  details: string[]; // array of strings representing paragraphs that describe the module to end users.
  links: { // relevant links about the module
    label: string; // link's name
    link: string; // URL
  }[];
  parameters: { // module's dispaly parameters, chosen by its creator as relevant for dispaly to end users
    label: string; // parameter's name
    functionName: string; // name of the view or pure function that gets the parameter value
    displayType: string; // a free-text field that tells front ends how to generate a proper UI component for the parameter
  }[];
  type: { // type of module
    eligibility: boolean;
    toggle: boolean;
    hatter: boolean;
  };
  implementationAddress: string; // module's implementation address, equal in every network
  deployments: { // networks the implementation is deployed and supported
    chainId: string; // chain's ID
    block: string; // block number of the deployment transaction
  }[];
  creationArgs: ModuleCreationArgs; // the arguments that are passed to the module factory's creation function
  customRoles: Role[]; // module's custom roles
  writeFunctions: WriteFunction[]; // module's write functions
  abi: Abi; // module's ABI
}
```

Check out the [Types](../v1-sdk/subgraph/types.md) section for more info about  Module's object properties .

### <mark style="color:purple;">getAllModules</mark>

Get all available modules (both active and deprecated).

```typescript
const modules = hatsModulesClient.getAllModules();
```

_**Response**_:

```typescript
{ [id: string]: Module }
```

An object that maps between module IDs and the corresponding module objects. A module ID is its implementation address.

### <mark style="color:purple;">getAllActiveModules</mark>

Get all the active modules (without deprecated ones).

```typescript
const activeModules = hatsModulesClient.getAllActiveModules();
```

_**Response**_:

```typescript
{ [id: string]: Module }
```

An object that maps between module IDs and the corresponding module objects. A module ID is its implementation address.

### <mark style="color:purple;">getAllEligibilityModules</mark>

Get all available eligibility modules.

```typescript
const eligibilityModules = hatsModulesClient.getAllEligibilityModules();
```

_**Response**_:

```typescript
{ [id: string]: Module }
```

An object that maps between eligibility module IDs and the corresponding module objects. A module ID is its implementation address.

### <mark style="color:purple;">getAllToggleModules</mark>

Get all available toggle modules.

```typescript
const toggleModules = hatsModulesClient.getAllToggleModules();
```

_**Response**_:

```typescript
{ [id: string]: Module }
```

An object that maps between toggle module IDs and the corresponding module objects.A module ID is its implementation address.

### <mark style="color:purple;">getAllHatterModules</mark>

Get all available hatter modules.

```typescript
const hatterModules = hatsModulesClient.getAllHatterModules();
```

_**Response**_:

```typescript
{ [id: string]: Module }
```

An object that maps between hatter module IDs and the corresponding module objects. A module ID is its implementation address.

### <mark style="color:purple;">getModuleById</mark>

Get a module object by its ID.

```typescript
const module = hatsModulesClient.getModuleById(moduleId);
```

_**Arguments**_:

```typescript
string
```

Module's ID (implementation address).

_**Response**_:

<pre class="language-typescript"><code class="lang-typescript"><strong>Module | undefined
</strong></code></pre>

The module that matches the provided ID, or `undefined` in case no matching module was found.

### <mark style="color:purple;">getModuleByImplementation</mark>

Get a module object by its implementation address.

```typescript
const module = hatsModulesClient.getModuleByImplementation(address);
```

_**Arguments**_:

```typescript
`0x${string}`
```

Module's implementation address.

_**Response**_:

<pre class="language-typescript"><code class="lang-typescript"><strong>Module | undefined
</strong></code></pre>

The module that matches the provided address, or `undefined` in case no matching module was found.

### <mark style="color:purple;">getModuleByInstance</mark>

Get the module object of an instance.

```typescript
const module = await hatsModulesClient.getModuleByInstance(address);
```

_**Arguments**_:

```typescript
`0x${string}`
```

Module's instance address.

_**Response**_:

<pre class="language-typescript"><code class="lang-typescript"><strong>Module | undefined
</strong></code></pre>

The module that matches the provided address, or `undefined` in case no matching module was found.

### <mark style="color:purple;">getModulesByInstances</mark>

Get the module objects of instances.

```typescript
const modules = await hatsModulesClient.getModulesByInstances(addresses);
```

_**Arguments**_:

```typescript
`0x${string}`[]
```

Addresses of the module instances.

_**Response**_:

<pre class="language-typescript"><code class="lang-typescript"><strong>(Module | undefined)[]
</strong></code></pre>

The modules matching the provided addresses. For every address that is not an instance of a registry module, the corresponding return value in the array will be 'undefined'.

### <mark style="color:purple;">getFactory</mark>

Get the Hats Module Factory metadata object.

```typescript
const factory = hatsModulesClient.getFactory();
```

_**Response**_:

```typescript
Factory
```

Factory's metadata object, see its type [here](../hats-modules/modules-sdk/types.md#factory).
