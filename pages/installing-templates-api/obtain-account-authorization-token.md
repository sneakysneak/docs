---
title: Obtain Account Authorization Token
sidebar: cyclr_sidebar
permalink: obtain-account-authorisation-token.html
tags: [installing]
---

# Obtain Account Authorization Token #

**_In order to perform operations against your end user accounts in Cyclr, a User Account OAuth token is required._**

User Account OAuth tokens are used to perform operations within the scope of an Account.

<table>
    <tr>
        <th>client_id</th>
        <td>Your Client Id, obtained from Console > Settings > OAuth Client Credentials</td>
    </tr>
    <tr>
        <th>client_secret</th>
        <td>The Account Id that you use to perform operations in</td>
    </tr>
    <tr>
        <th>grant_type</th>
        <td>The string “password“</td>
    </tr>
    <tr>
        <th>username</th>
        <td>An Account User’s username</td>
    </tr>
    <tr>
        <th>password</th>
        <td>An Account User’s password</td>
    </tr>
</table>

Response:

        200 OK

        {
            "access\_token": "0000000000000000000000000000000000000000000000000000000000000000",
            "token\_type": "bearer",
            "expires\_in": 1209599,
            "refresh\_token": "0000000000000000000000000000000000000000000000000000000000000000",
            "userName": "newAccountUser",
            "clientId": "jiK5IEHXfr96NFY76MHYlIaLpatGf7gm",
            ".issued": "Wed, 06 Dec 2017 16:06:32 GMT",
            ".expires": "Wed, 20 Dec 2017 16:06:32 GMT"
        }

Store the returned access_token and refresh_token for future use.

[How to List Available Templates](./get-list-available-templates)