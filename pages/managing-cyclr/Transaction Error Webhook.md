---
title: Transaction Error Webhook
sidebar: cyclr_sidebar
permalink: transaction-error-webhook
tags: [error,webhook]
---

Cyclr can be configured to make an HTTP Request if an error occurs in a running Cycle as a way of alerting you or your support staff.

This is performed as an HTTP POST Request to a URL you specify and contains JSON structured data in its Request Body.  Examples of this data can be found [here](./notifications).

The URL could be for an external system, or for a Webhook Step in a Template or Cycle within your Cyclr Partner, allowing you to process the data using Decision Steps, etc as you would any other data in Cyclr.  You could install a **Slack** or **SendGrid** Connector as a way to alert you and perhaps one of the database Connectors to log the data as well.

If you choose to use a Template or Cycle for this, you should install the **Error Webhook** Connector which knows the structure of the Request Body so is simpler to setup than using a standard **Generic Webhook** Connector's **Webhook** Method.


### Handling these Errors within Cyclr

1. We'd recommend creating a separate Folder perhaps called "Monitoring" to put your Template or Cycle into.  It's up to you whether you do this in your Cyclr Console as a Template or create a new Account dedicated to these sorts of tasks.
2. Install the **Error Webhook** Connector - it has a **Webhook** Method which knows the structure of Cyclr's error Requests.
3. Add that Connector's Webhook Step to your Cycle.
4. In the Webhook's Step Setup, copy the `Webhook URL`.
5. Go to your Cyclr Console, and select `Settings` > `General Settings`.
6. Tick the box for `Enable Transaction Error Webhook`
7. Paste in the URL you copied in Step 4.
8. Click Save.

Now you can go back to the Cycle where you added the Webhook Step, and add any Decision Steps, etc to filter how errors will be handled.

In the example below, any errors relating to "Account 12345" will trigger a message in Slack.

![](/images/triggerslackfromerror.png)


### Account-level Override

If you wish, you can choose to handle errors in particular Cyclr Accounts differently by using the Account-level override.

In your Cyclr Console, go to the Accounts menu then Account Management, click Settings for the Account you wish to set this for and use the **Transaction Error Webhook** options.
