---
title: Creating a new Account using the Cyclr API
sidebar: cyclr_sidebar
permalink: overview-new-account
tags: 
---

This article gives an overview on setting up a new Cyclr Account using the Cyclr API.

See the [Cyclr Concepts article](./cyclr-concepts) for an explanation of some of the terms used here.


### Accessing Cyclr's API

You'll need to obtain an Access Token from Cyclr's API to be able to make calls to it.

This is described in [API Authentication](./cyclr-api-authentication).



### Create an Account

Typically, each of your business' clients will have their own Cyclr Account to store their data and integrations (Cycles) to keep them separate from your other clients' data.

To create a new Cyclr Account, you would call the ```POST /v1.0/accounts``` API endpoint as described [in this article](./create-account).



### Install any common Account Connectors

You might wish to add an Account Connector for your own system in every Account when you create it.  You may be expecting your clients to work with the data you hold for them.  If so, you can install this straightaway by providing the authentication details your system requires.

To do this, you call one of the ```POST /v1.0/connectors/.../install``` API endpoints.

To identify your Connector within Cyclr so you can specify it in an ```POST /v1.0/connectors/.../install``` call,  make a Request to the ```GET /v1.0/connectors``` endpoint using the ```query``` QueryString parameter to search for your Connector and confirm its Name (and Version, if set).


Depending on the Authentication mechanism of your Connector (ApiKey, OAuth 1.0/2.0, Basic, etc) you'll need to [provide the authentication details to Cyclr differently](./authenticate-account-connector).



### Installing Templates

Once you have an Account, you can install Templates into it for any standard integrations you wish the client to use.

You can see what's available by calling the ```GET /v1.0/templates``` endpoint to [list available Templates](./list-available-templates).

You can then [install a Template](./install-from-template) by calling ```POST /v1.0/templates/{id}/install```.
