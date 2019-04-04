---
title: Notifications
sidebar: cyclr_sidebar
permalink: notifications
tags: [embedding]
---

Cyclr is able to send notification emails to account administrators when there is an issue with an account's cycles, or to call a webhook, perhaps to alert another system.

This can be set up in your Cyclr Console by going to the **Settings** menu in the top right then **Integration Settings**.

There are 3 options:

* Enable User Notification Emails
* Enable Notification Webhook
* Notification Webhook URL (shown when Enable Notification Webhook is ticked)




**Example Webhook Notification**

    {
      "accountId": "00000000-0000-0000-0000-000000000000",
      "title": "Cycle Error: Example Cycle",
      "message": "There was an error when we were running your cycle: Example cycle. We have paused it for now."
    }

*   **accountId** – the ID of the account that the notification is for
*   **title** – a short title for the notification
*   **message** – the notification message

[Setting Up API Authentication ](./api-authentication)
