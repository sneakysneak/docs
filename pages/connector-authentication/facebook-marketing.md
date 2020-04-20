---
title: Facebook Marketing Authenticaiton
sidebar: cyclr_sidebar
permalink: facebook-connector
tags: [connector]
---

# Facebook Marketing API #

Partner Setup
-------------

Facebook Marketing API uses OAuth 2. You should sign up for an application on Facebook first and get an OAuth client ID and client secret.

Here is the official documentation for creating a Facebook app:

[https://developers.facebook.com/docs/apps/register](https://developers.facebook.com/docs/apps/register)

1.  Log into your Facebook account.
2.  Create a Facebook Developer account if you don’t already have one: [https://developers.facebook.com/](https://developers.facebook.com/)
3.  Create a new Facebook App: [https://developers.facebook.com/apps/](https://developers.facebook.com/apps/)

    Below are the details you should provide:

    **Name**: your application name

    **App Domain**: your Cyclr **Service Domain**, e.g. "app-h.cyclr.com". This can be found in your Cyclr Console under Settings > Integration Settings > Service Domain.

    **Facebook Login > Settings > Valid OAuth Redirect URIs**: you may need to add ths Facebook Login as a Product to your App, or Facebook may already have automatically added it for you.
    Set the **Valid OAuth Redirect URIs** option to your Cyclr **Service Domain** plus "/connector/callback", e.g.:
    
    ```https://app-h.cyclr.com/connector/callback```
    
    If you miss this step, you'll see the following error message when trying to install the Connector in Cyclr:
    
    ```Can't load URL: The domain of this URL isn't included in the app's domains. To be able to load this URL, add all domains and sub-domains of your app to the App Domains field in your app settings.```

4.  Go to Cyclr Console (https://my.cyclr.com/console) > Connectors > Connector Library > Facebook Marketing API > Setup

    **Client ID**: This is the App ID displayed after you create the Facebook app

    **Client Secret**: This is the App Secret displayed after you create the Facebook app

5.  Don’t forget to make your Facebook app public. It’s in Development by default.

Your Facebook Marketing API connector is now set up! You can test it by installing it in one of your user accounts.

API Integration Guide
---------------------

Facebook Marketing API uses OAuth 2 Authorisation Code flow. It requires your end users to sign into Facebook and grant Cyclr access to their account.

To do this, call _/UpdateAccountConnectorOAuth_ with a one-time sign-in token.
