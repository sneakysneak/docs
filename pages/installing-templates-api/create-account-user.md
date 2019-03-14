---
title: Create Account User
sidebar: cyclr_sidebar
permalink: create-account-user
tags: [installing]
---

**_Users exist in Cyclr either to enable your end users to access our user interface directly, or for your app to access a Cyclr account on their behalf via our REST API._**

A user should be created and given access to the new Account, so that we can generate an authorization token to work on objects, Connectors and Cycles, within the Account.

    PUT /v1.0/accounts/{Account ID}/users

    {
      "UserName": "newAccountUser",
      "Password": "Password123"
    }

Response:

    200 OK

If Enable User Login Page is enabled under _Console > Settings > Integration Settings_, the supplied credentials can be used by the user to login to the account at example-h.cyclr.com

[How to Obtain an Account OAuth Token](./obtain-account-authorization-token)