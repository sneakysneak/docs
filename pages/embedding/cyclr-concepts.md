---
title: Cyclr Concepts
sidebar: cyclr_sidebar
permalink: cyclr-concepts
tags: [embedding]
---

### Connectors

A Connector is a Cyclr implementaion of a third party API.  When installed into an Account it provides connectivity with the third party application.

* * *

### Account Connector

Account Connectors are installed instances of Connectors that hold additional authentication details required for connectivity to the third party application.

* * *

### Accounts

Accounts allow the grouping of Account Connectors and the Cycles that use them.

* * *

### Users

Users can be given access to Accounts, allowing them to install and modify the Account Connectors and Cycles.

* * *

### Integration Templates

Integration Templates are pre-made integrations that can be installed by Users into Accounts as Cycles.

* * *

### Cycles

Cycles are integrations in an Account that when activated will perform the integration flow. Cycles can be triggered on a scheduled interval or by a webhook event in a third party application.

* * *

### Cycle Transaction

A Cycle Transaction is created each time a Cycle is triggered.  It segregates the request and response data relating to each Cycle Step from other data, allowing the Cycle to have multiple Transactions in progress simultaneously.

* * *

### Cycle Step

A Cycle is made up of a collection of Cycle Steps.  Each Cycle Step may connect with a third party API to send and/or receive data, perform a logic action such as delaying the Cycle Transaction for a period of time, or perform different actions depending on the data received from the third party API.
