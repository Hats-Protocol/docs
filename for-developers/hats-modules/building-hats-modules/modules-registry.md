# Modules Registry

Creating new modules is important, but they really only come to life when users of Hats Protocol can attach them to hats. We've built several tools to help developers put modules in the hands of users.

* [Modules Registry](https://github.com/Hats-Protocol/modules-registry)
* [Modules SDK](../modules-sdk/)

## Modules Registry

The Hats Modules Registry is a curated modules database. Tools, apps, and platforms in the Hats ecosystem — including the [Modules SDK](../modules-sdk/) — use it as the source of truth for safe, high quality modules they can serve to users and other developers.&#x20;

Today, the primary consumer of the registry is the Modules SDK, which is used by the [Hats App](https://app.hatsprotocol.xyz/) to enable users to easily discover, configure, and attach modules to hats.

### Submit a module to the registry

To submit a module to the registry, open a pull requests to the [registry repo](https://github.com/Hats-Protocol/modules-registry). You will need the following information for your submission:

* Module name
* Module description
* The module's Github repo and repo owner/org
* The module type: eligibility, toggle, and/or hatter
* Implementation contract address
* Deployments to the implementation address, including chain ID and block number
* The list of immutable args, with name, description, type, and example for each
* The list of mutable args (initData), with name, description, type, and example for each
* The module's ABI

For more specifics on the submission requirements, see the [registry repo README](https://github.com/Hats-Protocol/modules-registry/blob/main/README.md).

### Governance

The registry is currently governed and curated by the Hats Protocol core team. Over time, however, curation will decentralize to the wider Hats community.

{% hint style="info" %}
Modules do not need to be on the registry to be compatible at the protocol level. Hats Protocol itself is fully permissionless. The registry is a separate mechanism.
{% endhint %}

