# Get Available Modules

The following functions are used in order to get available modules, as exist in the [Modules Registry](../hats-modules/building-hats-modules/modules-registry.md).

Modules are represented as Module objects, with the following type:

```typescript
{
  name: string; // module's name 
  details: string[]; // module's details, separated to paragraphs
  links: { // relevant links, including module's source code
    label: string; // link's title/description
    link: string; // link's URL
  }[];
  parameters: { // module's parameters to display
    label: string; // parameter's title/description
    functionName: string; // function to query in order to get the paramaeter's value
    displayType: string; // type of value for display purpose
  }[];
  type: { // type of module
    eligibility: boolean;
    toggle: boolean;
    hatter: boolean;
  };
  implementationAddress: string; // deployed implementation 
  deployments: { // implementation deployment block per chain
    chainId: string;
    block: string;
  }[];
  creationArgs: 
    immutable: { // immutable args for new module instance creation
      name: string; // arg's name
      description: string; // short description
      type: string; // solidity type (e.g. "uint256")
      example: unknown; // example arg 
      displayType: string; // type of value for display purpose
    }[];
    mutable: {
      name: string; // arg's name
      description: string; // short description
      type: string; // solidity type (e.g. "uint256")
      example: unknown; // example arg 
      displayType: string; // type of value for display purpose
    }[];
  };
  abi: Abi; // module's ABI
}
```

### <mark style="color:purple;">getAllModules</mark>

Get all available modules.

```typescript
const modules = hatsModulesClient.getAllModules();
```

_**Response**_:

```typescript
{ [id: string]: Module }
```

An object that maps between module IDs and the corresponding module objects. A module ID is the `keccak256` hash of the module object.

### <mark style="color:purple;">getAllEligibilityModules</mark>

Get all available eligibility modules.

```typescript
const eligibilityModules = hatsModulesClient.getAllEligibilityModules();
```

_**Response**_:

```typescript
{ [id: string]: Module }
```

An object that maps between eligibility module IDs and the corresponding module objects. A module ID is the `keccak256` hash of the module object.

### <mark style="color:purple;">getAllToggleModules</mark>

Get all available toggle modules.

```typescript
const toggleModules = hatsModulesClient.getAllToggleModules();
```

_**Response**_:

```typescript
{ [id: string]: Module }
```

An object that maps between toggle module IDs and the corresponding module objects. A module ID is the `keccak256` hash of the module object.

### <mark style="color:purple;">getAllHatterModules</mark>

Get all available hatter modules.

```typescript
const hatterModules = hatsModulesClient.getAllHatterModules();
```

_**Response**_:

```typescript
{ [id: string]: Module }
```

An object that maps between hatter module IDs and the corresponding module objects. A module ID is the `keccak256` hash of the module object.

### <mark style="color:purple;">getModuleById</mark>

Get a module object by its ID.

```typescript
const module = hatsModulesClient.getModuleById(moduleId);
```

_**Arguments**_:

```typescript
moduleId: string
```

`moduleId` - Module's ID (`Keccak256` of the module object).

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
address: string
```

`address` - Module's implementation address.

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
address: `0x${string}`
```

`address` - Module's instance address.

_**Response**_:

<pre class="language-typescript"><code class="lang-typescript"><strong>Module | undefined
</strong></code></pre>

The module that matches the provided address, or `undefined` in case no matching module was found.
