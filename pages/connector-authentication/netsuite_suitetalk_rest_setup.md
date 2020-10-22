---
title: Oracle NetSuite - SuiteTalk REST Web Services Connector Guide
sidebar: cyclr_sidebar
permalink: netsuite-suitetalk-rest-connector
tags: [connector]
---

Oracle NetSuite - SuiteTalk REST Web Services connector is authenticated with the OAuth2.0 protocol. You will need to register an application and provide the connector with that application's Client ID (Application ID), Client Secret and your Account ID.

## NetSuite Setup

Firstly [log in](https://system.netsuite.com/pages/customerlogin.jsp) to your NetSuite account.

### Creating An App

1. From the top navigation bar go to **Setup** > **Integration** > **Manage Integrations** > **New**

2. Enter a name for the app

3. "State" should be "Enabled"

4. From the Authentication section select **OAuth2.0**, enter your Redirect URI and select the scope **REST WEB SERVICES**

   > Redirect URI should be {% raw %}https://{{Your Cyclr service domain e.g. app-h.cyclr.com}}/connector/callback{% endraw %}

5. Make sure that neither **Token-based Authentication** or **User Credentials** are selected

6. Scroll down and click **Save**

You will be presented with your Client ID and Client Secret. Make a note of these as they will only be shown once.

### Finding Your Account ID

1. From the top navigation bar go to **Setup** > **Company** > **Company Information**

![Company information](./images/netsuite_suitetalk_1.png)

### Enable OAuth2.0 For Your Account

1. From the top navigation bar go to **Setup** > **Company** > **Enable Features**

2. Click the **SuiteCloud** subtab

3. In the **SuiteScript** section check **Client SuiteScript** and **Server SuiteScript**

4. In the **SuiteTalk (Web Services)** section check make sure **REST Web Services**, **RESt Record Service (Beta)** and **REST Query Service (Beta)** are checked

5. In the **Manage Authentication** section, check the **OAuth 2.0** box

6. Scroll to the bottom of the page and click **Save**

## Connector Setup

1. Locate the Oracle NetSuite - SuiteTalk REST Web Services connector

   > Cyclr Console > Connectors > Connector Library > Oracle NetSuite - SuiteTalk REST Web Services

2. From the Edit Connector interface click 'Setup'

3. Enter your Client ID, Client Secret and Account ID

4. Click **Next**

5. Click **Sign In**

6. A new window will open prompting you to log in to your NetSuite account

7. You will be presented with the message "The application is requesting permission to access..."

8. Click **Continue**

You should now have been redirected to Cyclr which means that the connector is authenticated and ready to use.
