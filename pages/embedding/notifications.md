---
title: Notifications and Transaction Error Handling
sidebar: cyclr_sidebar
permalink: notifications
tags: [embedding]
---

Cyclr can be set to make an HTTP call when there is an issue with an account's cycles or an error occurs in a transaction.

This can be set up in your Cyclr Console by going to the **Settings** menu in the top right then **Integration Settings**.

There are 4 options:

* Enable Notification Webhook
* Notification Webhook URL (shown when Enable Notification Webhook is ticked)
* Enable Transaction Error Webhook
* Transaction Error Webhook URL (shown when Enable Transaction Error Webhook is ticked)


**Example Notification Webhook Payload**
```json
{
  "accountId": "00000000-0000-0000-0000-000000000000",
  "title": "Cycle Error: Example Cycle",
  "message": "There was an error when we were running your cycle: Example cycle. We have paused it for now."
}
```

*   **accountId** – the ID of the account that the notification is for
*   **title** – a short title for the notification
*   **message** – the notification message



**Example Transaction Error Webhook Payload**<br />
The information in the **Detail** property will contain the Response that was received so will change dependent on the API being called and how it formats its error Responses.  If there are specific errors you wish to handle, you may need to force them to occur so that you can view the Response to see how that appears.
```json
{
    "Timestamp": "2019-08-08T11:25:34.0412055Z",
    "AccountId": "a2b35322-c966-4a29-95d7-065aaf12b127",
    "CycleId": "15643129-a29d-4957-865c-0495099fbbec",
    "StepId": "519713ff-57cf-49ef-9c00-f3a3e1569268",
    "TransactionId": "1564aae4-b82e-4712-a078-30a4e53c40d0",
    "Message": "Failed to call the method",
    "Detail": "404 Item not found\r\n{\"Code\":200,\"Message\":\"Item not found\"}\r\n\r\n\r\nHTTP Request:\r\nGET https://someapi.com/getitems/myID/ HTTP/1.1\r\nAccept: application/json\r\nApiKey:\r\nUser-Agent: Cyclr\r\nUser-Agent: (https://cyclr.com)"
}
```




[Setting Up API Authentication ](./api-authentication)
