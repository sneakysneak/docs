---
title: Microsoft Azure Active Directory Connector Guide
sidebar: cyclr_sidebar
permalink: azure-ad-connector
tags: [connector]
---

## Authentication

The Microsoft Azure Active Directory connector is authenticated with the OAuth2.0 protocol. You will need to register an application and provide the connector with that application's Client ID (Application ID) and Client Secret.

Please follow Microsoft's official guide to registering an applciation in Azure Active Directory. That documentation can be found [here](https://docs.microsoft.com/en-us/azure/active-directory/develop/quickstart-register-app).

- For "Supported account types" you should select "Accounts in any organizational directory (Any Azure AD directory - Multitenant)"
- Redirect URI should be {% raw %}https://{{Your Cyclr service domain e.g. app-h.cyclr.com}}/connector/callback{% endraw %}
- Client ID (Application ID) is displayed in the overview of your created app
- Generate a Client Secret by following [these steps](https://docs.microsoft.com/en-us/azure/active-directory/develop/quickstart-register-app#add-a-client-secret)

Permissions must be set for the application:

1. From **App registrations** in the Azure portal select your application
2. Select **API permissions** from the menu on the left
3. Click **+ Add a permission**. This will open the permissions menu
   ![add permission button](./images/permissions_4.png)
4. From **Microsoft APIs** select **Microsoft Graph** and then **Delegated permissions**
   ![permissions menu](./images/permissions_1.png)
   ![permissions menu 2](./images/permissions_2.png)
5. You will be presented with a series of permissions categories
6. Select the checkboxes for the appropriate permissions and click **Add permissions**
   ![checked permission](./images/permissions_5.png)
   > Note: The initial release of the Microsoft Azure Active Directory connector only supports the retrieval of User and Group objects. Therefore the permissions set should be **offline_access**, **Directory.Read.All**, **Group.Read.All**, **GroupMember.Read.All** and **User.Read.All**
7. You must then **Grant admin consent for _orgnanisation_**
   ![grant admin consent](./images/permissions_3.png)

### Connector Setup

1. Locate the Microsoft Azure Active Directory connector

   > Cyclr Console > Connectors > Connector Library > Microsoft Azure Active Directory

2. From the Edit Connector interface click 'Setup'

3. Enter your Client ID and Client Secret, click 'Next'

4. Click 'Sign In'

5. A new window will open prompting you to log in, select your Azure account and authorize access to the connector

The connector is now authenticated and ready to use.
