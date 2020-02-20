---
title: Microsoft Dynamics Custom Objects
sidebar: cyclr_sidebar
permalink: dynamics-custom-connector
tags: [connector]
---

# Dynamics CRM Custom Objects Connector Setup #

This connector is designed to work with a single custom entity. When working with more than one, you must install a separate Dynamics CRM connector for each custom entity type.

### Installation

For details on how to authenticate this connector click [here](dynamics-crm-online.md). See the image below for an example:

When setting up the connector you will also have to enter the names of the custom entity set and custom entity type you wish to interact with. 

![](../images/dynamics_custom_objects_updated_1.png)

The request or response fields for the specified custom entity will now be auto-mapped for each method (request fields for the CREATE/UPDATE methods, response fields for GET methods). 

Example:

![](../images/dynamics_custom_objects_updated_2.png)

You can edit the **Display Names** to preference but **do not** edit the **Field Location** or **Data Type**, doing so will cause mapping errors. You can remove any fields you do not wish to retrieve/post using the dustbin button to the right of the field.

![](../images/dynamics_custom_objects_updated_3.png)
