---
title: Connector Authentication
sidebar: cyclr_sidebar
permalink: connector-authentication
tags: [connector-creation]
---

## Authentication Types

Cyclr supports various authentiction types and, with on occation the addition of scripting, it is possible to establish a connection with any API.

| Property | Description |
| --- | --- |
| ApiKey | The user should provide an API key as the HTTP header for the connector.|
| Basic  | The API uses HTTP basic authentication. |
| OAuth1 | The API uses OAuth 1.0a authentication. Requires: _ClientId _(also known as ConsumerKey), _ClientSecret _(also known as ConsumerSecret), _RequestTokenUrl_, _AuthorizeUrl_, _AccessTokenUrl_.|
| Auth2 | The API uses OAuth 2 authentication. Requires: _ClientId_, _ClientSecret_, _AuthoriseUrl_, _AccessTokenUrl_. |
| None | No authentication required.|
| AuthFields | the API needs to inject authentication fields into the POST message. Requires: _Name_, _Key_, _Type_. |

## OAuth2Type

Thess fields will only be used if the AuthType is OAuth2.

*   **AuthorisationCode (Default)** – the client will redirect the user to the authorization server, the user will then be asked to login to the authorization server and approve the client.
*   **ClientCredentials** – client will get the access token from the authorization server without user challenge.
*   **PasswordCredentials** – client will get the access token from the authorization server using username & password.

