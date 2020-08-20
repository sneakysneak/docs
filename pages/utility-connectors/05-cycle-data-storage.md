---
title: Cycle Data Storage
sidebar: cyclr_sidebar
permalink: cycle-data-storage
tags: [utility-connector]
---

## Purpose

If you need to store some data in a Cycle which you'll need later in that same Cycle, this Utility Connector can be used.  Data can be written in one part of the Cycle and retrieved in another.

Any data that is stored in the Connector will only be accessible by the Cycle that wrote it.

The **Cycle *Data* Storage** Connector works using simple Key and Value pairs.  The Key is unique and is used to set and get the Value.

If you wish to store more structured data or more than one value (perhaps the firstname, lastname, etc of a contact), you should use the **[Cycle *Object* Storage](./cycle-object-storage)** Connector as it allows multiple values to be stored as a single "object" against a Key value.

## Usage

[How To Use](./data-storage-usage) Cycle Data Storage.

## Related Topics

[Global Data Storage](./global-data-storage) 
[Cycle Object Storage](./cycle-object-storage)
