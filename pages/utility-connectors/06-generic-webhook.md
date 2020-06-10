---
title: Generic Webhook
sidebar: cyclr_sidebar
permalink: generic-webhook
tags: [utility-connector]
---

## Purpose

The Generic Webhook allows you to trigger a Cycle using inbound HTTP POST when an application connector does not include a method specific to the requirement.

Each instance of the Generic Webhook uses a unique URL to which the POST should be made.  You will need to define the request body fields as Custom Fields when setting up the connector (see below)/

## Passing Control between Integration Cycles

The Generic webhook can be used to link Cycles together.  A step in Cyclr 1 can make a POST to a Webhook that has been set up to trigger Cycle 2.

To set this up you will need to add custom fields to the the Generic Webhook connector (see below).  The same fields will been to be added to both the POST in the HTTP Methods section and to the Webhook in the Webhooks section.

You should then build both Cycles or Templates.  Whe you add the Webhook trigger to Cycle 2 you will be given the URL to which the post should be made.  This should be copied to the set up of the POST in Cycle 1 and added as the step setup mappings.

In testing of running this kind of structure you must start Cycle 2 before Cycle 1.  If you don't do this there is the danger that the webhok receiver is not active before the POST has been made.

In this example 2 Cycles have been used but the same procedure can be set up to chain together a whole series of Integrations.

## Related Topics

[How to add custom fields](./adding-custom-fields) 
