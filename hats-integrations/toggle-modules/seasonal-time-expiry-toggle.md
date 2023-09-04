---
description: >-
  Making hats automatically expire after a certain period of time, unless they
  are explicitly renewed
---

# Seasonal/ Time-Expiry Toggle

The Seasonal/ Time-Expiry Toggle Module (SeasonToggle for short) is a mechanistic Hats Protocol Toggle module — i.e. a contract that implements the [`IHatsToggle` interface](https://github.com/Hats-Protocol/hats-protocol/src/Interfaces/IHatsToggle.sol) — that allows an organization to configure certain hats to be automatically toggled off after a given interval, i.e. a "season".

## **Overview**

Organizational structure should not be permanent. By automatically turning off hats by default, SeasonToggle helps ensure that organizations continuously and explicitly revisit their own structure.&#x20;

In Hats Protocol, hats can be configured with Toggle modules that programmatically control whether and when the hat is active or inactive. SeasonToggle adds an automatic expiry for a group of hats within a given branch of an organization's hat tree, unless an admin of that branch explicitly extends it to a new season.

Usage of SeasonToggle involves the following phases:

1. **Setup**: create a new instance of SeasonToggle for the relevant branch of the hat tree
2. **Extension**: renew the branch of hats for a new season

Once in operation, Hats Protocol will retrieve hat status (active or inactive) from an instance of SeasonToggle by calling the `SeasonToggle.getHatStatus()` function.

The module's code is open source and is available [here](https://github.com/Hats-Protocol/season-toggle).

## **Using the Seasonal / Time-Expiry Toggle Module**

_This toggle module is currently in beta. Contact us at support \[at] hatsprotocol \[dot] xyz if you want to explore this module, or check out the Seasonal / Time-Expiry Toggle Github repo_ [_here_](https://github.com/Hats-Protocol/season-toggle)_._
