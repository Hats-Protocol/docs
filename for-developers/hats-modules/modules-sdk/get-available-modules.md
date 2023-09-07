# Get Available Modules

The SDK contains methods to get the available modules together with all the necessary information about each one, as a Module object:

```typescript
{
  name: string; // module's name 
  description: string; // short description
  github: { // module's source code location 
    owner: string;
    repo: string;
  };
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
  args: 
    immutable: { // immutable args for new module instance creation
      name: string; // arg's name
      description: string; // short description
      type: string; // solidity type (e.g. "uint256")
      example: unknown; // example arg 
    }[];
    mutable: {
      name: string; // arg's name
      description: string; // short description
      type: string; // solidity type (e.g. "uint256")
      example: unknown; // example arg 
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

### <mark style="color:purple;">getFunctionsInModule</mark>

Get a module's functions from its ABI.

```typescript
const module = hatsModulesClient.getFunctionsInModule(moduleId);
```

_**Arguments**_:

```typescript
moduleId: string
```

`moduleId` - Module's ID.

_**Response**_:

```typescript
{
  name: string;
  type: "write" | "read";
  inputs: { name: string | undefined; type: string }[];
}[]
```

An array of objects, each containing a function's information:

* `name` - The function's name.
* `type` - "read" for "view" and "pure" functions, "write" otherwise.
* `inputs` - Array of inputs for the function. For each input, contains its name, and its Solidity type.
