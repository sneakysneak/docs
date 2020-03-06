---
title: Salesforce Service Cloud Connector Guide
sidebar: cyclr_sidebar
permalink: salesforce-service-cloud-connector
tags: [connector]
---

## Salesforce Interface

#### OAuth Scopes

To porperly integrate this connector with your Salesforce App you must first select the appropriate scopes within the Salesforce interface:

1. Go to 'Setup' (gear icon in upper right corner) > 'Apps' (left hand menu) > 'App Manager'

2. Select the App you are connecting with Cyclr

3. Select 'Edit'

4. Scroll down to the API (Enable OAuth Setting) category

5. From 'Selected OAuth Scopes' > 'Available OAuth Scopes' select both 'Full access (full)' and 'Perform requests on your behalf at any time (refresh_token, offline_access)

6. Click the 'Add' button to add these to the 'Selected OAuth Scopes' list

   ![salesforce oauth scopes](./images/salesforce_oauth_scopes.png)

7. Scroll down and click 'Save'

It can take up to 10 minutes for these scope changes to take effect on the Salesforce server so we advise you wait at least 10 minutes before authenticating the connector.

## Connector Setup

1. Locate the Salesforce Service Cloud connector in the Cyclr console.

   > Cyclr Console > Connectors > Connector Library > Salesforce Service Cloud

2. Click the open padlock and on the next page enter the following information:

   | Name          | Description                                                                           |
   | ------------- | ------------------------------------------------------------------------------------- |
   | Client ID     | Your Salesforce Connected Apps 'Consumer Key'                                         |
   | Client Secret | Your Salesforce Connected Apps 'Consumer Secret'                                      |
   | Subdomain     | The subdomain of your Salesforce account. (eg. https://{Subdomain}.my.salesforce.com) |
