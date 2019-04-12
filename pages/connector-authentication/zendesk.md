---
title: Zendesk Webhooks
sidebar: cyclr_sidebar
permalink: zendesk-connector
tags: [connector]
---

Webhook Implementation - Closed Tickets
---------------------------------------

  - set Trigger conditions to 'Status' is 'Closed' and/or 'Solved' 
  - in 'Actions' set 'Notify Target' to required Target 
  - fields below to be added to Trigger in 'JSON Body'  

```json

{ 
  "TicketId":"\{\{ticket.id}}", 
  "ExternalId":"\{\{ticket.external_id}}", 
  "Title":"\{\{ticket.title}}", 
  "Description":"\{\{ticket.description}}", 
  "TicketVia":"\{\{ticket.via}}", 
  "Status":"\{\{ticket.status}}", 
  "Priority":"\{\{ticket.priority}}", 
  "Type":"\{\{ticket.ticket_type}}" 
}
```


For further information please check the official Zendesk documentation:

(https://support.zendesk.com/hc/en-us/articles/204890268)
