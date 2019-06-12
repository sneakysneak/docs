---
title: Obtain a Partner Authorization Token
sidebar: cyclr_sidebar
permalink: obtain-partner-authorization-token
tags: [installing]
---

_**Before a new user and account can be created in Cyclr, a Console admin user OAuth token must be obtained.**_

Partner OAuth tokens are used to perform operations within the scope of the Partner Console.

Request:

    POST https://yourCyclrInstance/oauth/token
    Content-Type: application/x-www-form-urlencoded
    
    client_id=XXXXXXXXXXXXXXXXXXXX&grant_type=password&username=me@example.com&password=myPassword

<table>
  <tr>
    <th>yourCyclrInstance</th>
    <td>Your Cyclr instance URL.<br />This could be one of the following: api.cyclr.com if your Cyclr account is hosted on our US instance; api.cyclr.uk if it's on our UK instance; your own domain if your Cyclr instance is self-hosted.</td>
  </tr>    
  <tr>
    <th>client_id</th>
    <td>Your Client ID, obtained from Console > Settings > OAuth Client Credentials</td>
  </tr>
  <tr>
    <th>grant_type</th>
    <td>The string "password"</td>
  </tr>
  <tr>
    <th>username</th>
    <td>A Console Administrator's username</td>
  </tr>
  <tr>
    <th>password</th>
    <td>The Console Administrator's password</td>
  </tr>
</table>

Response:

    200 OK
    {
         "access_token": "0000000000000000000000000000000000000000000000000000000000000000",
         "token_type": "bearer",
         "expires_in": 1209599,
         "refresh_token": "0000000000000000000000000000000000000000000000000000000000000000",
         "userName": "me@example.com",
         "clientId": "XXXXXXXXXXXXXXXXXXXX",
         ".issued": "Wed, 06 Dec 2017 15:31:50 GMT",
         ".expires": "Wed, 20 Dec 2017 15:31:50 GMT"
    }

Store the returned tokens for future use. The access token is used to authenticate all other Cyclr API requests, the refresh token can be used to get a new access token when it expires. See [API Authentication](../embedding/api-authentication).

[How to Create an Account](./create-account)
