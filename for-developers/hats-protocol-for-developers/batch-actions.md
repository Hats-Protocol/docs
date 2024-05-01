# Batch Actions

In addition to [batch create](creating-hats.md#batch-creation) and [batch mint](minting-hats.md#batch-minting), any set of Hats.sol functions can be batched together into a single transaction.

This is made possible by [Multicallable](https://github.com/Vectorized/solady/blob/main/src/utils/Multicallable.sol) — from which Hats.sol inherits — which adds a non-payable `multicall` function to the contract. This enables EOAs to make multiple calls to the contract atomically, unlocking a number of useful batch operations that were previously only available to smart contracts.

For example,&#x20;
