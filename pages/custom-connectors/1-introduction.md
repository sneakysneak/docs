---
title: Connector Introduction
sidebar: cyclr_sidebar
permalink: connector-introduction
tags: [connector-creation]
---

## What is a custom connector?

A custom connector allows you to integrate apps that aren’t in our [connector library](http://cyclr.com/connectors/). You can even add connectors for your own private apps and websites. Our Connector Manager makes this task quicker and easier to maintain than writing a traditional coded integration.  Note that not all price plans include access to the Custom Connector builder or that access is subject to an additional fee

A connector a standardised definition in a propriatory Cyclr format of the methods and fields of an API. Once created Cyclr takes care of everthing that is needed to work with an API including:

*   **Descrption** – Name, description vwerion etc.
*   **Authentication** – how the connector should connect to the target API (e.g. OAuth, API key, login, etc).
*   **Rate limiting & Throttling** - how frequetly it is allowed to make calls to the API. 
*   **Properties** - the description, version, icon, etc.
*   **Methods** – the endpoints for the API.
*   **Fields** – the fields used in the methods.
*   **Parameters and Triggers** – if the method requires parameters, mergefields, or internal look-up methods.
*   **Paging** – how the application works with large data sets when multiple calls are required to access all the required data.
*   **Scripting** – JavaScript can be added to take care of any special requirements in the API.

If available in your console, access to Custom Connectors is available in the Console under 'Connectors'.
