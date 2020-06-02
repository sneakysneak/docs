---
title: Adding Custom Fields
sidebar: cyclr_sidebar
permalink: adding-custom-fields
tags: [templates]

---

## Manually Adding Custom Fields

By default, connectors will only include the standard fields used by an application. Where you need to work with additional fields in the application you are connecting to, it is possible to add these using custom fields.

![](./images/connector-custom-field.gif)

To add a custom field:

*   From the builder’s sidebar, click to expand the app connector and click Settings
*   In the section named Methods and Fields, click to expand the category and then the method you wish to add fields to
*   Under Request Fields or Response, click the + button to add a field

The following needs to be specified

| Property | Description |
| --- | --- |
| Field Location | This is the field name as used by the API. Often this is just a case of copying the syntax of the existing fields. |
| Display Name | This is the “friendly” name as it will be shown in the user interface. |
| Description | You can optionally describe the field and provide documentation, for example how it is used. |
| Data Type | You can optionally define a data type for your field.  If it is datetime then add the subtype to allow for type conversions between differnt standards. |
