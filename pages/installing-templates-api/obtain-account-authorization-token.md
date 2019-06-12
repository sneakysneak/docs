---
title: Obtain an Account Authorization Token
sidebar: cyclr_sidebar
permalink: obtain-account-authorization-token
tags: [installing]
---

User Account OAuth tokens are used to perform operations within the scope of an Account.

Request:

    POST https://yourCyclrInstance/oauth/token
    Content-Type: application/x-www-form-urlencoded
    
    client_id=XXXXXXXXXXXXXXXXXXXX&client_secret=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXX&grant_type=password&username=me@example.com&password=myPassword

<table>
  <tr>
    <th>yourCyclrInstance</th>
    <td>Your Cyclr instance URL.<br />This could be one of the following: "api.cyclr.com" if your Cyclr account is hosted on our US instance; "api.cyclr.uk" if it's on our UK instance; your own domain if your Cyclr instance is self-hosted.</td>
    </tr>
    <tr>
        <th>client_id</th>
        <td>Your Client Id, obtained from Console > Settings > OAuth Client Credentials</td>
    </tr>
    <tr>
        <th>client_secret</th>
        <td>The Account Id of the Account to work in.<br />Can be obtained by calling Accounts API endpoint to view a list of all Accounts, or in your web browser through the Console by viewing the Settings of the Account and taking the accountId value from the web browser's address bar.</td>
    </tr>
    <tr>
        <th>grant_type</th>
        <td>The string "password"</td>
    </tr>
    <tr>
        <th>username</th>
        <td>An Account User's username</td>
    </tr>
    <tr>
        <th>password</th>
        <td>An Account User's password</td>
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
        ".issued": "Wed, 06 Dec 2017 16:06:32 GMT",
        ".expires": "Wed, 20 Dec 2017 16:06:32 GMT"
    }

Store the returned access_token and refresh_token for future use.

[How to List Available Templates](./get-list-available-templates)
