---
title: Zoho
sidebar: cyclr_sidebar
permalink: zoho
tags: [connector]
---

# Zoho #

## Partner Setup ##

This document explains how to setup access to Zoho and to install the Zoho CRM Connector.

### OAuth Setup ###

You'll need to register your Cyclr Partner with Zoho by creating a "Client" in your [Zoho API Console](https://accounts.zoho.com/developerconsole).

[Zoho's own documentation on this can be found here](https://www.zoho.com/accounts/protocol/oauth-setup.html)


* When asked which **Client Type** you wish to create, choose "Server-based Application".

![](./images/Zoho_ClientType.png)

* Enter an **Authorized Redirect URI** using this format:

```https://{{Your Cyclr Service Domain}}/connector/callback```<br />

e.g. ```https://app-h.cyclr.com/connector/callback```

You can find your **Service Domain** within your Cyclr Console from the **Settings** menu then **General Settings**.

### Connector Setup ###

Once you have your Client ID and Client Secret from Zoho, go to your Cyclr Console then Connectors > Application Connector Library, search for **Zoho CRM**, click the Padlock button next to it and set them so they're used when installing the Connector.
