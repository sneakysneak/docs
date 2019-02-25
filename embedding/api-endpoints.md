---
title: API Endpoints
---

# API Endpoints #

Note: You need to have authenticated with the Cyclr API before you can use these methods.

List Accounts
-------------

Gets a list of the accounts owned by the partner.

**Request**

    GET https://my.cyclr.com/api/partner/accounts

**Response**

    [
      {
        "Id": "00000000000000000000000000000000",
        "Name": "Demo Account",
        "Description": "This account is used for demos.",
        "PricePlanId": 2,
        "LastBillDate": "2017-02-09T16:23:08",
        "NextBillDate": "2017-03-09T16:23:08",
        "AuditInfo": "Demo"
      }
    ]

Partner Details
---------------

Gets details about the partner.

**Request**

    GET https://my.cyclr.com/api/partner/details

**Response**

    {
      "AnonymousAccountsEnabled":true,
      "ApplicationDisplayName":"Example Partner",
      "ApplicationIcon":"data:image/png;base64,...",
      "AppStyle":null,
      "ComingSoonConnectorsEnabled":true,
      "CustomConnectorsEnabled":true,
      "CycleNoun":"Cycle",
      "CycleSharingEnabled":true,
      "Domain":"partner.example.com",
      "IntercomAPIKey":null,
      "IntercomAppId":null,
      "IntercomSecretKey":null,
      "HeaderHtml":null,
      "FooterHtml":null
    }

Create Account
--------------

Creates a new Cyclr account in the partner.

**Request**

    POST https://my.cyclr.com/api/partner/createaccount
    
    {
      "Name": "Demo Account",
      "Description": "This account is used for demos.",
      "Timezone": "Europe/London",
      "PricePlanId": 2,
      "NextBillDate": "2017-03-09T16:23:08",
      "AuditInfo": "Demo"
    }

**Response**

    {
      Id: "00000000000000000000000000000000"
    }

Update Account
--------------

Updates an existing Cyclr account in the partner.

**Request**

    PUT https://my.cyclr.com/api/partner/accounts/{{AccountId}}
    
    {
      "Name": "New Demo Account",
      "Description": "",
      "Timezone": "Europe/London",
      "PricePlanId": 3,
      "NextBillDate": "2017-03-10T16:23:08",
      "AuditInfo": "Demo"
    }

{{AccountId}}: ID of the account to update.All the fields in the request body are optional.**  
Response**

    {
      Id: "00000000000000000000000000000000"
    }

Get Account Signin Token
------------------------

Creates a sign in token, that can be used to sign in a partner application user to a cyclr partner account.

**Request**

    POST https://my.cyclr.com/api/partner/createaccountsignintoken
    
    {
      "AccountId": "00000000000000000000000000000000",
      "Username": "user@example.com"
    }
    

**Response**

    {
      "ExpiresAtUtc": "2016-11-18T10:50:45.6509216Z",
      "Token": "0000000000000000000000000000000000000"
    }
    

User can be signed in by directing them to before the expiry.

    http://my.cyclr.com/account/signinwithtoken?token={Token}

Install Connector
-----------------

Installs a connector in the selected account.

If the connector is using an API key to authenticate, please provide a valid **ApiKey** in the request.

Similarly, if the connector requires **username **and **password**, please provide them in the request body.

This method does not support connectors which require an OAuth authentication flow.

**Request**

    POST https://my.cyclr.com/api/partner/installconnector
    
    {
      "AccountId": "0000000000000000000000000000000000000",
      "ConnectorName": "Connector",
      "ConnectorVersion": "v1",
      "InstalledName": "Demo Connector",
      "ApiKey": "api-key"
    }
    
    or
    
    {
      "AccountId": "0000000000000000000000000000000000000",
      "ConnectorName": "Connector",
      "ConnectorVersion": "v1",
      "InstalledName": "Demo Connector",
      "Username": "user",
      "Password": "password"
    }

**Response**

    200 OK

Get Price Plans
---------------

Get a list of available price plans.

**Request**

    GET https://my.cyclr.com/api/partner/priceplans

**Response**

    [
      {
        "Id": "2",
        "Name": "Starter"
      },
      {
        "Id": "3",
        "Name": "Pro"
      }
    ]

Get Account Usage
-----------------

Get the amount of tasks and the maximum number of cycles an account has used in a monthly period.

**Request**

    GET https://my.cyclr.com/api/partner/accounts/{{AccountId}}/billing?fromDate={{FromDate}}

{{AccountId}}: ID of the account to get account usage for.{{FromDate}}: Optional date to get account usage from, for example, 2016-12-09. If this parameter is left empty, it will return account usage since the last billing date.**  
Response**

    {
      "TaskCount": 1623,
      "CycleCount": 10,
      "FromDate": "2016-12-09T16:23:08",
      "ToDate": "2017-01-08T16:23:08",
      "CurrentPricePlanId": 3,
      "AuditInfo": "Demo"
    }

