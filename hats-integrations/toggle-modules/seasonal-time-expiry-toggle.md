---
description: >-
  Making hats automatically expire after a certain period of time, unless they
  are explicitly renewed
---

# Seasonal/ Time-Expiry Toggle

A Hats Toggle module that allows an organization to configure certain hats to be automatically toggled off after a given interval, i.e. a "season".

## **Overview**

Organizational structure should not be permanent. By automatically turning off hats by default, SeasonToggle helps ensure that organizations continuously and explicitly revisit their own structure.&#x20;

In Hats Protocol, hats can be configured with Toggle modules that programmatically control whether and when the hat is active or inactive. SeasonToggle adds an automatic expiry for a group of hats within a given branch of an organization's hat tree, unless an admin of that branch explicitly extends it to a new season.

Usage of SeasonToggle involves the following phases:

1. **Setup**: create a new instance of SeasonToggle for the relevant branch of the hat tree
2. **Extension**: renew the branch of hats for a new season

The module's code is open source and is available [here](https://github.com/Hats-Protocol/season-toggle).

## **Using the Seasonal / Time-Expiry Toggle Module**

* Go to the tree that includes the hat you wish to create the module for
* Select "Edit Tree"
* Locate and select the hat
* Open the "Deactivation & Reactivation" section

<figure><img src="../../.gitbook/assets/Deactivation And Reactivation.png" alt=""><figcaption></figcaption></figure>

* Choose "Automatically" and then choose "Create new Module". This will open the module creation form

<figure><img src="../../.gitbook/assets/Create Toggle Module.png" alt=""><figcaption></figcaption></figure>

* Choose "Create new Module"

<figure><img src="../../.gitbook/assets/Create Module 2 (1).png" alt=""><figcaption></figcaption></figure>

* Choose "Season Toggle" in the module type

<figure><img src="../../.gitbook/assets/Season Toggle Guide.png" alt=""><figcaption></figcaption></figure>

* Fill in the module-specific parameters
* Choose "Deploy & Return" to deploy the module and return to the hat edit form
