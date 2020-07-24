---
title: Xero OAuth2.0 Authentication
sidebar: cyclr_sidebar
permalink: xero-oauth2
tags: [connector]
---

# Xero (OAuth2.0)

## Partner Setup

In order to install a **Xero (OAuth2.0)** Connector, you must first create a Xero OAuth 2.0 **App** in Xero's Developer portal.

### Preparation 

When creating your Xero App, you will need to provide your Cyclr Partner **Service Domain** so it's best to have that information to hand before you begin.

This is specific to your instance of Cyclr and can be found in your Cyclr Partner Console under **Settings > General Settings > Service Domain**.

Your Cyclr Partner may have been setup with a default Service Domain, but this can be changed if you would prefer to remove mentions of 'cyclr' from it.  Contact Support for more.

### Creating a Xero App

Go to [https://developer.xero.com/myapps] to create a Xero OAuth 2.0 App in Xero.

Click the **New app** button in the top right to see a form similar to this:

![](./images/xero_oauth20_newapp.png)

Leave the **grant type** as "Auth code" and complete the rest of the fields.

For the **OAuth 2.0 redirect URI**, enter your Cyclr Service Domain in this format:
```
https://[Your Cyclr Service Domain]/connector/callback
```


After successfully submitting the form, you'll see an **OAuth 2.0 credentials** section.

Click the **Generate a secret** option to create a new Client Secret:

![](./images/xero_oauth20_credentials.png)

You should now take your Client ID and Client Secret values and store them in your Cyclr Console against the Xero (OAuth2.0) entry.

### Cyclr Setup

From your Cyclr Console, click the **Connectors** option along the top then **Application Connector Library**, find **Xero (OAuth2.0)** - you may need to use the Search box to locate it - then click the Padlock button and paste and save your values there.

You should now be able to successfully install a **Xero (OAuth2.0)** Connector.

At this point it would be a good idea to install a Connector and run a test against one of the Methods, just to make sure the authentication process has been completed successfully.
