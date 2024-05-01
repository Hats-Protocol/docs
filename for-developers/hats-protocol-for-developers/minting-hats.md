# Minting Hats

Only a hat's admin(s) can mint its token to a wearer.

To mint a hat:

1. The hat must be active
2. Its max supply must not have already been reached
3. The target wearer must not already wear the hat, and&#x20;
4. If the hat's eligibility module is mechanistic, the target wearer must be eligible for the hat

A hat's admin can mint its token individually by calling `Hats.mintHat`.

#### **Batch Minting**

An admin can also mint multiple hats by calling `Hats.batchMintHats`. This enables an admin to mint instances of the same hat to multiple wearers, to mint several hats at once, or even to mint an entire hats tree it just created.
