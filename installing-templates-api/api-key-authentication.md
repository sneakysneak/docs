---
title: API Key Authentication
---

# API Key Authentication #

_**For connectors that are authenticated using an API key provided by the 3rd party app.**_

Your user’s API Key will need to be collected in your application and sent to Cyclr like below, this can be done for both unauthenticated and authenticated connectors.

    PUT /v1.0/account/connectors/{Account Connector ID}
    {
        "AuthValue": "0000000000000000000000000000000000000000"
    }

Response:

    {
        "Id": 36328,
        "Name": "Pipedrive",
        "Description": null,
        "AuthValue": "f3f1736d3c4c587469a7ba06558d744ec8f32ec3",
        "Authenticated": true,
        "Connector": {
            "Id": 2550,
            "Name": "Pipedrive",
            "Description": "Sales CRM for small teams with big ambitions. This connector authenticates you via an API key.",
            "Status": "Approved",
            "Version": "1.0",
            "Icon": null,
            "AuthDescription": null,
            "AuthType": "ApiKey",
            "OAuth2Type": "Unknown",
            "AuthScheme": null
        },
        "IsPartnerIntegrationConnector": false,
        "Properties": [],
        "CustomFields": []
    }

[HTTP Basic Authentication](./basic-authentication)  
[OAuth Authentication](./oauth-authentication)  
[Step Setup](./step-set-up)