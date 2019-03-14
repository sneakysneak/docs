---
title: Obtain a Partner Authorization Token
sidebar: cyclr_sidebar
permalink: obtain-partner-authorization-token
tags: [installing]
---

_**Before a new user and account can be created on Cyclr, a Console admin user OAuth token must be obtained.**_

The token request should be POSTed in a application/x-www-form-urlencoded content type.

    POST /oauth/token

<table>
  <tr>
    <th>client_id</th>
    <td>Your Client Id, obtained from Console > Settings > OAuth Client Credentials</td>
  </tr>
  <tr>
    <th>grant_type</th>
    <td>The string “password“</td>
  </tr>
  <tr>
    <th>username</th>
    <td>A Console Administrator’s username</td>
  </tr>
  <tr>
    <th>password</th>
    <td>The Console Administrator’s password</td>
  </tr>
</table>

Example response:

    200 OK
    {
         "access_token": "0000000000000000000000000000000000000000000000000000000000000000",
         "token_type": "bearer",
         "expires_in": 1209599,
         "refresh_token": "0000000000000000000000000000000000000000000000000000000000000000",
         "userName": "noreply@cyclr.com",
         "clientId": "00000000000000000000000000000000",
         ".issued": "Wed, 06 Dec 2017 15:31:50 GMT",
         ".expires": "Wed, 20 Dec 2017 15:31:50 GMT"
    }

Store the returned tokens for future use. The access token is used to authenticate all other Cyclr API requests, the refresh token can be used to get a new access token when it expires. See [API Authentication](../embedding/api-authentication).

[How to Create an Account](./create-account)