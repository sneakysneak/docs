---
title: Slack Authentication
sidebar: cyclr_sidebar
permalink: slack
tags: [connector]
---

# Partner Setup #


Slack uses OAuth 2.0 for authentication and you must first [register your Cyclr Partner with Slack](https://api.slack.com/apps) to obtain your Client ID and Client Secret values.

From https://api.slack.com/apps click the Create an App button then enter:
*  **App Name** - a name for your App.  This will be shown on-screen when users install the Slack Connector.
*  **Development Slack Workspace** - which Slack Workspace your App belongs to.  This just gives it a "home" and doesn't prevent it from being installed in other people's workspaces.

![Slack - Create an App](./images/slack-create-an-app.png)

After you've created your App, set the **Redirect URLs** under the **Add features and functionality** section's **Permissions** button:

![Slack - Permissions](./images/slack-permissions.png)

**Redirect URL**: you must add 2 callback URLs to allow Intercom to be used in your Cyclr Console templates as well as your Cyclr accounts.

These URLs are:

*   {% raw %}https://{{Your Cyclr console domain e.g. my.cyclr.com or my.cyclr.uk}}/connector/callback{% endraw %}
*   {% raw %}https://{{Your Cyclr service domain e.g. app-h.cyclr.com}}/connector/callback{% endraw %}

Your Cyclr Partner **Service Domain** can be found in your Cyclr Console under Settings > Integration Settings.

![Slack - Redirect URLs](./images/slack-redirect-urls.png)
