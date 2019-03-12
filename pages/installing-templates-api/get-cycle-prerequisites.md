---
title: Get Cycle Prerequisites
sidebar: cyclr_sidebar
permalink: get-cyclr-prerequisites.html
tags: [installing]
---

**_A Cycle installed in an Account from a Template may have prerequisites that need to be fulfilled before the Cycle can be activated._**

The Cyclr API can provide information on the prerequisites for a Cycle to run.

    GET /v1.0/cycles/{Cycle Id}/prerequisites
    Authorization Bearer 2890edffcb964e8aab038cf4efc340ab62a4f604bd5a41369654086f5bd25519

Response

    200 OK
    [{
        "ReasonCode": 20,
        "Reason": "Unauthenticated connector",
        "ObjectType": "AccountConnector",
        "ObjectId": 36328
    },
    {
        "ReasonCode": 20,
        "Reason": "Unauthenticated connector",
        "ObjectType": "AccountConnector",
        "ObjectId": 36329
    },
    {
        "ReasonCode": 30,
        "Reason": "Missing mapping",
        "ObjectType": "Action",
        "ObjectId": "709b68ba-394e-4339-9550-abd0312e8dd5"
    }]

In this example, there are the following pre-requisites:

*   Two Connectors that are unauthenticated
*   A Step with a missing field mapping

[How to Authenticate Account Connector](./account-connector-authentication)