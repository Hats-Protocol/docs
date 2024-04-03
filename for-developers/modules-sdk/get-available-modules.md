# Get Available Modules

The following functions are used in order to get available modules, as exist in the [Modules Registry](../hats-modules/building-hats-modules/modules-registry.md).

See the Module type [here](../hats-modules/modules-sdk/types.md#module).

### <mark style="color:purple;">getModules</mark>

Get all available modules, optionally use a filter function in order to retrieve only a subset of the modules.

```typescript
const modules = hatsModulesClient.getAllModules();
```

_**Arguments**_:

```typescript
filter?: (module: Module) => boolean
```

An optional filter function. For each [Module](../hats-modules/modules-sdk/types.md#module), should return `true` if the module should be included, `false` otherwise.

_**Response**_:

```typescript
{ [id: string]: Module }
```

An object that maps between module IDs and the corresponding module objects. A module ID is its implementation address.

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

The modules matching the provided addresses. For every address that is not an instance of a registry module, the corresponding return value in the array will be `undefined`.
