---
title: Microsoft Azure DevOps Connector Guide
sidebar: cyclr_sidebar
permalink: azure-devops-connector
tags: [connector]
---

## Authentication

The Microsoft Azure DevOps connector is authenticated with the OAuth2.0 protocol. You will need to register an application and provide the connector with that application's Client ID (Application ID) and Client Secret.

Register an oAuth [here](https://app.vsaex.visualstudio.com/app/register)

- Authorization callback URL should be `https://{{Your Cyclr service domain e.g. app-h.cyclr.com}}/connector/callback`
- Authorized Scope should ONLY be "Work items (full)", if other scopes are entered you will not be able connect
- App ID, App Secret and Client Secret are displayed in the overview of your created app. Please copy these somewhere safe.

Log into your [DevOps portal](https://dev.azure.com/) to obtain your organization ID and project ID that you wish to connect. 

### Connector Setup

1. Locate the Microsoft Azure DevOps connector in the portal

2. Under the partner console in the connecotor list you can enter the client ID and secret. Alternativly the client will be asked to enter the client id and secret when the connector is installed.

3. Enter your Client ID (App ID) and Client Secret (Client Secret)

4. When the connector is installed enter Organization and Project, click 'Next'

5. Click 'Sign In'

6. A new window will open prompting you to log in, select your Azure account and authorize access to the connector

The connector is now authenticated and ready to use.

For reference the full Azure Dev Ops Authentication documentation can be found [here](https://docs.microsoft.com/en-us/azure/devops/integrate/get-started/authentication/oauth?view=azure-devops).

