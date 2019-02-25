---
title: Notifications
---

# Notifications #

Cyclr sends notification emails to account administrators when there is an issue with an accounts cycles. You can instead get notifications posted to a webhook.

**Example Notification**

    {
      "accountId": "00000000-0000-0000-0000-000000000000",
      "title": "Cycle Error: Example Cycle",
      "message": "There was an error when we were running your cycle: Example cycle. We have paused it for now."
    }

*   **accountId **– the ID of the account that the notification is for
*   **title **– a short title for the notification
*   **message **– the notification message

[Setting Up API Authentication ](./api-authentication)
