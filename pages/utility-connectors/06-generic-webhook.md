---
title: Generic Webhook
sidebar: cyclr_sidebar
permalink: generic-webhook
tags: [utility-connector]
---

## Purpose

The **Generic Webhook Connector** provides all the typical HTTP Methods, such as **GET**, **POST** and **DELETE**, allowing you to make HTTP Requests towards remote systems.

It also provides a **Webhook** Method that can be used to trigger a Cycle from an inbound HTTP POST Request.  Useful if an application connector does not include a method specific to that requirement.

Each instance of the Webhook Method uses a unique URL to which a POST Request can be made.  You will need to define the Request body fields as Custom Fields when setting up the connector (see below).

As with all connectors, the **Generic Webhook** Connector can be added multiple times and setup and named appropriately for each use case.

## Passing Control between Cycles

The **Generic Webhook** Utility Connector can be used to link Cycles together.  For example, a step in Cycle 1 can make an HTTP POST to a Webhook that has been set up as a trigger to start Cycle 2.

This linking of Cycles might be done when an integration is large and complex, and splitting it into smaller units will improve maintainability.  It might also be done when the same processing needs to be run in a number of situations, and linking is preferable to duplicating the same sequence of steps in multiple Cycles.

To set this up you will need to add custom fields to the Generic Webhook connector for the information that will be passed between the Cycles (see below).  The same fields will need to be added to both the 'POST' in the HTTP Methods section and to the 'Webhook' in the Webhooks section of the Connector Settings.

You should then build both Cycles (or Templates) before making the linkage.  When you add the Webhook trigger to Cycle 2 you will be given the URL it will use to listen for inbound Requests.  This should be entered as the URL Field in Step Setup of the POST Step in Cycle 1.

When testing or running this kind of 'linked Cycles' structure you must start Cycle 2 before Cycle 1.  If you do not do this there is a danger that the webhook receiver will not be active before the first POST is made.

In this example, 2 Cycles have been used but the same procedure can be set up to chain together a whole series of Cycles.

## Related Topics

[How to add custom fields](./adding-custom-fields) 
