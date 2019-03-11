---
title: Authenticate Account Connector
sidebar: cyclr_sidebar
permalink: authenticate-account-connector.html
tags: [installing]
---

# Authenticate Account Connector #

_**You users will be required to provide authentication information before Cycles can be run.**_

Cyclr supports three types of connector authentication:

<table>
    <tr>
        <th>API Key</th>
        <td>Your user will provide an API Key from the third party application that gives access to the third party API</td>
    </tr>
    <tr>
        <th>HTTP Basic</th>
        <td>Your user will provide a username and password to access the third Party API</td>
    </tr>
    <tr>
        <th>OAuth</th>
        <td>Your user will be taken through an OAuth flow which will generate a token that can be used to generate the third party API</td>
    </tr>
</table>

For each connector requiring authentication, take your user through the appropriate flow.

Check the authentication type that the installed Account Connector requires.

    GET /v1.0/account/connectors/36328
    Authorization Bearer 2890edffcb964e8aab038cf4efc340ab62a4f604bd5a41369654086f5bd25519

Response:

    {
        "Id": 36328,
        "Name": "Pipedrive",
        "Description": null,
        "AuthValue": nul ,
        "Authenticated": false,
        "Connector": {
            "Id": 2550,
            "Name": "Pipedrive",
            "Description": "Sales CRM for small teams with big ambitions. This connector authenticates you via an API key.",
            "Status": "Approved",
            "Version": "1.0",
            "Icon": null,
            "AuthDescription": null,
            "AuthType": "**ApiKey**",
            "OAuth2Type": "Unknown",
            "AuthScheme": null
        },
        "IsPartnerIntegrationConnector": false,
        "Properties": [],
        "CustomFields": []
    }

In this example, the AuthType for this Account Connector is ApiKey.

The response also confirms that the Account Connector is not yet authenticated (“Authentication”: false).

[API Key Authentication](./api-key-authentication)  
[HTTP Basic Authentication](./basic-authentication)  
[OAuth Authentication](./oauth-authentication)