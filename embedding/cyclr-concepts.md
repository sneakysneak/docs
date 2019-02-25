---
title: Cyclr Concepts
---

# Cyclr Concepts #

### Connectors

A Connector is a Cyclr implementaion of a third party API that when installed into an Account will provide connectivity with the third party application.

* * *

### Account Connector

Account connectors are installed instances of Connectors that support additional authentication details required for connectivity with the Users third party application account(s).

* * *

###  Accounts

Accounts allow the grouping of Account Connectors & the Cycles that use them.

* * *

### Users

Users can be given access to Accounts, they can then install/modify the Account Connectors & Cycles.

* * *

### Integration Templates

Integration Templates are pre-made integrations that can be installed by Users into Accounts as Cycles.

* * *

### Cycles

Cycles are integrations in an Account that when activated will perform the integration flow. Cycles can be triggered on a scheduled interval or by a webhook event in a third party application.

* * *

### Cycle Transaction

A Cycle Transaction is created each time a Cycle is triggered, it segregates the request& response data from each Cycle Step from each other allowing the Cycle to have multiple transactions in progress simultaneously.

* * *

### Cycle Step

A Cycle is made up of a collection of Cycle Steps, each step either connects with a third party API to send/recivie data or performs a logic action such as delaying the Cycle Transaction or performing diferent actions depending on the data received from the third party API.
