---
title: Generic Webhook
sidebar: cyclr_sidebar
permalink: generic-webhook
tags: [utility-connector]
---

## Purpose

The Generic Webhook allows you to trigger a Cycle using inbound HTTP POST when an application connector does not include a method specific to the requirement.

Each instance of the Generic Webhook uses a unique URL to which the POST should be made.  You will need to define the request body fields as Custom Fields when setting up the connector (see below).

As will all connectors the Generic Webhook connector can be added multiple times and setup and named appropriatly to each use case.

## Passing Control between Integration Cycles

The Generic Webhook Utility Connector can be used to link Cycles together.  For example, a step in Cycle 1 can make an HTTP POST to a Webhook that has been set up as a trigger to start Cycle 2.

This linking of Cycles might be done when an integration is large and complex, and splitting it into smaller units will improve maintainability.  It might also be done then the same processing needs to be run in a number of situations, and linking is preferable to duplicating the same sequence of steps in multiple Cycles.

To set this up you will need to add custom fields to the Generic Webhook connector for the information that will be passed between the Cycles (see below).  Exactly the same fields will need to be added to both the 'POST' in the HTTP Methods section and to the 'Webhook' in the Webhooks section of the Connector settings.

You should then build both Cycles or Templates before making the linkage.  When you add the Webhook trigger to Cycle 2 you will be given the URL to which the post should be made.  This should be copied to the settings section of the POST in Cycle 1 and added to the field mappings.

When testing or running this kind of 'linked Cycles' structure you must start Cycle 2 before Cycle 1.  If you do not do this there is the danger that the webhook receiver will not active before the POST has been made.

In this example 2 Cycles have been used but the same procedure can be set up to chain together a whole series of Integrations.

## Related Topics

[How to add custom fields](./adding-custom-fields) 
