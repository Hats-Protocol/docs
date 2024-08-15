# Hat Details

## Overview

In Hats Protocol, each hat includes a [details field](https://github.com/Hats-Protocol/hats-protocol/blob/cccb71a061cdb9095af7d11dfdb47026993d8c4e/src/Hats.sol#L67), which is used for arbitrary metadata about the hat, such as a name, description, and other properties like authorities and responsibilities associated with the hat.

A common way to use this field is to store the data on IPFS as a JSON object, and set the hat's details field with the object's CID (Content Identifier). This method allows to add rich metadata about a hat, while keeping the gas costs minimal.&#x20;

This package provides utility function to handle hats details, by both pinning metadata JSON objects to IPFS and reading from it.&#x20;

It was designed to work both in the browser and in Node.js. You can find the source code [here](https://github.com/Hats-Protocol/details-sdk).

## Content

{% content-ref url="getting-started.md" %}
[getting-started.md](getting-started.md)
{% endcontent-ref %}

{% content-ref url="usage.md" %}
[usage.md](usage.md)
{% endcontent-ref %}
