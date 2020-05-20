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

Data is stored as Key/Value pairs.  There are options to:

#Set a Value
This will create a Key/Value pair.  An error will be returned if the Key already exists.
Get a 

## Related Topics

[Cycle Data Storage](./cycle-data-storage) 
