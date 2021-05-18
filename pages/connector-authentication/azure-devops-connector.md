---
title: Microsoft Azure DevOps Connector Guide
sidebar: cyclr_sidebar
permalink: azure-devops-connector
tags: [connector]
---

For reference, Microsoft's full Azure DevOps Authentication documentation can be found [here](https://docs.microsoft.com/en-us/azure/devops/integrate/get-started/authentication/oauth?view=azure-devops).

## Authentication

The Microsoft Azure DevOps Connector is authenticated using OAuth2.0. You will need to register an application and provide Cyclr with that application's Client ID (Application ID) and Client Secret.

Register an Application [here](https://app.vsaex.visualstudio.com/app/register)

Authorization callback URL should be 

`https://<Your Cyclr Service Domain e.g. app-h.cyclr.com>/connector/callback`
 
 Enter the appropriate scopes required for your usecase. We suggest at least adding "Work items (full)" as it is required for most methods (apart from Audit Logs and Accounts).
 
 [A list of available scopes can be found here](https://docs.microsoft.com/en-us/azure/devops/integrate/get-started/authentication/oauth?toc=%2Fazure%2Fdevops%2Forganizations%2Ftoc.json&bc=%2Fazure%2Fdevops%2Forganizations%2Fbreadcrumb%2Ftoc.json&view=azure-devops#scopes)
 
App ID, App Secret and Client Secret are displayed in the overview of your created app. Please keep a copy of these somewhere safe.

Log in to your [DevOps portal](https://aex.dev.azure.com/) to obtain your organization ID and project ID that you wish to connect to.

<img src="./images/AzureDevOps1.png" style="zoom:75%;" />

### Partner Setup

In your Cyclr Console, go to Connectors > Application Connector Library and locate the entry for Microsoft Azure DevOps.

You can either enter your Client ID (App ID) and Client Secret (Client Secret) in the entry or leave both blank before clicking Save.

If you leave them blank, the user must provide the values when installing the Connector.

### Connector Setup

1. When installing the Connector, enter Organization ID, Project Name and the list of scopes provided during application creation and then click 'Next'.

2. Click 'Sign In' and a new window will open prompting you to log in.

3. Select your Azure account and authorize access.

The connector is now authenticated and ready to use.

