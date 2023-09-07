# Versioning

HatsModule includes a single storage variable for versioning purposes.

```solidity
string public version_;
```

This variable is set in the constructor, which means that it has a value only in the implementation contract and not in any instances (since instance clones are not created with the constructor).

To get the version for a module instance use the [version](https://github.com/Hats-Protocol/hats-module/blob/5a69da357e70cc2e3727d6ec02097711439ec32b/src/HatsModule.sol#L56) function instead.

```solidity
function version() public view returns (string memory) {
    return HatsModule(IMPLEMENTATION()).version_();
}
```

### &#x20;
