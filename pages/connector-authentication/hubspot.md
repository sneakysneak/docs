---
title: Hubspot Connector Guide
sidebar: cyclr_sidebar
permalink: hubspot-connector
tags: [connector]
---

Hubspot Setup
---------------

For Cyclr to connect with the Hubspot API you will need to create an "Application" in the Hubspot account, as detailed below:

1. Login to the Hubspot Developer Portal [here](https://app.hubspot.com/signup-v2/developers)
2. Follow the Hubspot [documentation](https://developers.hubspot.com/docs/faq/how-do-i-create-an-app-in-hubspot) to create an application
3. In the `Auth` tab you will see a `Client ID` and `Client Secret`.  Make a note of these to use in the connector setup.
4. The Redirect URL should be https://<span></span>{service domain}/connector/callback. Your service domain can be found in your Cyclr console under `Settings > General Settings > Service Domain`.
5. It is not necessary to set any scopes, as these will be handled automatically by the connector.

Permissions
---------------
In order to use the Products and Line Items methods, the user must be assigned a [paid Sales Hub seat](https://knowledge.hubspot.com/articles/kcs_article/account/manage-sales-hub-and-service-hub-paid-users) within Hubspot.

Connector Setup
---------------

The Connector now can be installed using the credentials obtained in the above steps:

**Client ID**: `Client ID`

**Secret**: `Client Secret`

You will then be prompted to log in, select your Hubspot and authorize access to the connector.
