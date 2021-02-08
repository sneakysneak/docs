---
title: Collection Splitting
sidebar: cyclr_sidebar
permalink: collection-splitting
tags: [managing-cyclr]

---

If a cycle is going to be operating on a collection of data, you can choose to **split** the transaction into separate transactions for each record, or have one transaction for the entire collection.

This is useful in situations where a step in your cycle is drawing data from multiple different sources, and the source arrays are unconnected.

### Example use-case

If Cyclr doesn't detect a common value in each source array, you may be asked to select one in a pane similar to the one pictured:

![What unique field can join your data together?](./images/what-unique-field.png)

If there isn't a field (e.g. email address) that connects both sources, you may need to split one or more of the source arrays.

Settings for splitting can be found in the Cycle settings, and if necessary can be manually overridden in the advanced settings of a step.