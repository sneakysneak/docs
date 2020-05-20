---
title: Global Data Storage
sidebar: cyclr_sidebar
permalink: global-data-storage
tags: [utility-connector]
---

## Purpose

If there is the requirement to hold data permanenty in Cyclr account then you can use the Global Data Storage Connector.  Data persists beyon the life any any Integration Cycle in which it is added or ameded and can be accessed in subscequent runs of a Cycle or other Cycles within the same account.

## Usage

This connector can be installed multiple times, and each instance will have it's own associated data set.  When the connector is installed it is advisable to give it a name that reflects how it will be used.

Data is stored as Key/Value pairs.  There are options that operate on single records:-

### Set a Value
This will create a Key/Value pair if the Key does not already exist.  If it does exiss the current Value will be updated to the new Value you provide.

### Append Value
If the supplied Key value already exists then the new Value you provide will be appended to the current value.  If the Key does not exist a new entry is created.

### Get a Value
The Value field is returned for the specifed Key.

### Delete Key
Deletes a Key/Value Pair

There are options that operate on the whole data set:-

### Get All Vales
This is return all the records in the data set.

### Delete All Keys
This is remove all the entries in the data set.

## Related Topics

[Cycle Data Storage](./cycle-data-storage) 
