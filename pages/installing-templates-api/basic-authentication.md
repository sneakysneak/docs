---
title: HTTP Basic Authentication
sidebar: cyclr_sidebar
permalink: http-basic-authentication
tags: [installing]
---

_**For connectors that are authenticated HTTP basic authentication.**_

Your user’s username and password will need to be collected in your application and sent to Cyclr like below

Concat the username and password like “username:password”

Base64 encode the concated username and password “dXNlcm5hbWU6cGFzc3dvcmQ=”, use this as the value to send to Cyclr

    PUT /v1.0/account/connectors/36328
    {
        "AuthValue": "dXNlcm5hbWU6cGFzc3dvcmQ="
    }

Response:

    {
        "Id": 36328,
        "Name": "Pipedrive",
        "Description": null,
        "AuthValue": "dXNlbmFtZTpwYXNzd29yZA==",
        "Authenticated": true,
        "Connector": {
            "Id": 2550,
            "Name": "Pipedrive",
            "Description": "Sales CRM for small teams with big ambitions. This connector authenticates you via an API key.",
            "Status": "Approved",
            "Version": "1.0",
            "Icon": null,
            "AuthDescription": null,
            "AuthType": "Basic",
            "OAuth2Type": "Unknown",
            "AuthScheme": null
        },
        "IsPartnerIntegrationConnector": false,
        "Properties": [],
        "CustomFields": []
    }

[API Key Authentication](./api-key-authentication)<br/>[OAuth Authentication](./oauth-authentication)  
[Step Setup](./step-set-up)