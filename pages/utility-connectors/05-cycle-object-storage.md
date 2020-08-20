---
title: Cycle Object Storage
sidebar: cyclr_sidebar
permalink: cycle-object-storage
tags: [utility-connector]
---

## Purpose

If you need to store some data in a Cycle which you'll need later in that same Cycle, this Utility Connector can be used. Data can be written in one part of the Cycle and retrieved in another.

Any data that is stored in the Connector will only be accessible by the Cycle that wrote it.

The **Cycle *Object* Storage** Connector works using a Key that sets and gets a Value that can contain several separate properties.  These could be several pieces of data about a contact such as their firstname, lastname, etc.

If you only wish to store a single value, you could instead use the **[Cycle *Data* Storage](./cycle-data-storage)** Connector which works with simple Key and Value pairs.

## Installation

When installing this Connector, you're asked to provide a **Field List**.

This is a comma-separated list of the fields you intend to use.  Cyclr will automatically create them as Custom Fields on the **Add/Update Entry** and **Get All Entries** Methods.

You could enter ```firstname, lastname, dateofbirth``` for instance to create 3 separate Custom Fields to then map to in a Cycle.

If you wish to add additional Fields after you've installed the Connector, you can simply return to the Setup and modify the Field List.

## Usage

**Add/Update Entry** Method: either creates a new entry or updates an existing one using a unique Key and any values you've provided for the other Fields.

**Get All Entries** Method: returns all of the stored values in the context of the Cycle you're working in.

This Connector builds upon the features of the **Cycle Data Storage** Connector so supports most of the Methods documented here:

[Data Storage Usage](./data-storage-usage)

## Related Topics

[Global Data Storage](./global-data-storage)

[Cycle Data Storage](./cycle-data-storage)
