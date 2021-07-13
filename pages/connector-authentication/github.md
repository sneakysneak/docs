---
title: Github Authentication
sidebar: cyclr_sidebar
permalink: github-authentication
tags: [connector]

---

To use the GitHub connector you will need to set up an app within GitHub, to obtain a Client ID and Client Secret.

## Setting up your GitHub app

1. Go to https://github.com/settings/developers and click `New Oauth App`

    ![New Oauth App Button](./images/NewOauthAppButton.png)
2. Provide the following information:

    * **Application Name**: This name will be presented to your users when they grant your app access to their information.
    * **Homepage URL**: This should be <https://YourServiceDomain> (for example <https://megacorp-h.cyclr.com>)
    * **Authorization Callback URL** : This should be your Homepage URL plus /connector/callback, e.g. <https://megacorp-h.cyclr.com/connector/callback>

3. On the next screen note down your Client ID, and generate a Client Secret.

## Authenticating your GitHub Cyclr Connector

1. In your Console, access `Connectors` > `Application Connectors`

    ![Application Connectors](./images/ApplicationConnectors.png)

2. Search for GitHub, and click the `Setup Required` padlock.

    ![GitHub in Console](./images/GitHubInConsole.png)

3. In the next screen, enter your GitHub Client ID and Client Secret and `Save Changes`.

4. Your GitHub connector is now all set up, and you won't need to enter this information again when authenticating the connector.
