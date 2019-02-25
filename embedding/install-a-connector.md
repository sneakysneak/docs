---
title: Install a Connector
---

# Install a Connector #

This article will guide you through installing a connector into an account. You must have already have an access token to  
an account.

1.  [Getting the connector ID](#1)
2.  [Installing the connector](#2)
3.  [Authenticating OAuth connectors](#3)

* * *

### Getting the connector ID

You need the ID of a connector before you can install it. You can find a connector by calling the /v1.0/connectors endpoint, this will show the connectors that are available to the account.

#### Request

    GET https://api.cyclr.com/v1.0/connectors HTTP/1.1
    User-Agent: Fiddler
    Host: api.cyclr.com
    Authorization: Bearer ****************************************************************
    

JavaScript

#### Response

    [
       {  
          "Id":1,
          "Name":"Example Connector",
          "Description":"This is an example connector.",
          "Status":"Approved",
          "Version":"1.0",
          "Icon":"",
          "AuthDescription":"",
          "AuthType":"ApiKey",
          "OAuth2Type":"Unknown",
          "AuthScheme":null
       },
       {...}
    ]

JSON

* * *

### Installing the connector

Now that you have a connector ID, the connector can be installed by calling the /v1.0/connectors/{id}/install endpoint.

#### Body parameters

<table>
    <tr>
        <th>Name</th>
        <td>The name for the installed connector</td>
    </tr>
    <tr>
        <th>Description</th>
        <td>_(Optional)_ Any description for the installed connector</td>
    </tr>
    <tr>
        <th>AuthValue</th>
        <td>_(Optional)_ Authentication value for the third party API that will be used by the connector. Provide username  
and password as base64 (username:password), provide API keys as plain text. OAuth can only be provided if you  
have your own OAuth flow implementation. To use Cyclr’s implementation see the next step.</td>
    </tr>
</table>

* * *

#### Request

    POST https://api.cyclr.com/v1.0/connectors/1/install HTTP/1.1
    User-Agent: Fiddler
    Authorization: Bearer ****************************************************************
    Host: api.cyclr.com
    Content-Length: 49
    Content-Type: application/json
    
    {"Name":"Example", "AuthValue":"example-api-key"}

#### Response

    {  
       "Id": 1,
       "Name":"Example",
       "AuthValue":"example-api-key",
       "Authenticated":true,
       "Connector":{ ... },
       ...
    }

The connector is now installed into the account, if the connector doesn’t use OAuth you’re all done; otherwise, read on to authenticate with OAuth.

* * *

### Authenticating OAuth connectors

If the connector requires an OAuth authentication to work with the third party API, you will be required to show the user a popup that will take them through the OAuth flow. First you need to get an account one time sign in token, this will be used to allow a web browser to sign in using the credentials of the Oauth token.

#### Request

    POST https://api.cyclr.com/v1.0/accounts/tokens HTTP/1.1
    User-Agent: Fiddler
    Authorization: Bearer ****************************************************************
    Host: api.cyclr.com
    Content-Length: 0

#### Response

    {
      "Token":"***************************************",
      "ExpiresAtUtc":"2017-11-29T16:22:36.7257196Z"
    }

Now you have a sign in token you can build the URL to send the user too to begin the OAuth flow.

#### URL & Querystring

<table>
    <tr>
        <th>URL</th>
        <td>https://api.cyclr.com/web/connector/updateaccountconnectoroauth</td>
    </tr>
    <tr>
        <th>id</th>
        <td>This is the ID of the installed connector from the response when [installing the connector](#2).</td>
    </tr>
    <tr>
        <th>token</th>
        <td>The account sign in token. Remember to URI encode it.</td>
    </tr>
    <tr>
        <th>targetOrigin</th>
        <td>Specifies what the origin of the other window must be for the javascript callback event to be dispatched. If  
the callback message is null we will redirect to the targetOrigin.</td>
    </tr>
    <tr>
        <th>callbackMessage</th>
        <td>(Optional) Callback message to be sent to the parent window.</td>
    </tr>
</table>

#### Example built URL

    https://api.cyclr.com/web/connector/updateaccountconnectoroauth?id=1&token=***************************************&targetOrigin=example.com&callbackMessage=done

When the user is sent to the built URL they will be redirected to the third party OAuth flow. On completion they will be either redirected to targetOrigin or a JavaScript message will be posted to the parent window.
