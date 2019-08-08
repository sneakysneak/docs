---
title: Vincere Connector Guide
sidebar: cyclr_sidebar
permalink: vincere-connector
tags: [connector]
---

Vincere Setup
---------------

For Cyclr to connect with the Vincere API you will need to select a suitable user account within Vincere. This account will require setting up, the steps to complete this are below.

1. Login to Vincere Application (https://{{YourVincereDomain}}.vincere.io/loginForm.do)
2. Select Settings > Marketplace 
3. Select the API Tab
4. Click "Create new token" button, this will display the API KEY.
5. Click "Create new Client ID" button, this will display the Client ID
6. Enter the callback URL for Cyclr into the "Callback URL" field. "https://{{Your Cyclr console domain e.g. my.cyclr.com or my.cyclr.uk}}/connector/callback"
  * Your Cyclr domain, e.g. https://app-h.cyclr.com/. This can be found in your Cyclr Console under Settings > Integration Settings > Service Domain.


Connector Setup
---------------

The connector now can be configured using the credentials obtained in the above steps.

__Client ID__: _Vincere Client ID_

__Secret__: _Leave this blank_

__Domain__:  _yourcompanydomain_ (see your URL when accessing Vincere, https://yourcompanydomain.vincere.io)

__API Key__: _Vincere API Key_