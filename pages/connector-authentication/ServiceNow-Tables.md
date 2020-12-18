---
title: ServiceNow Table API
sidebar: cyclr_sidebar
permalink: service-now-tables
tags: [connector]

---

Partner Setup
---------------

The ServiceNow Table API makes use of Basic username and password credentials for remote API access. 

For your reference, [here](https://docs.servicenow.com/bundle/london-application-development/page/integrate/inbound-rest/concept/c_RESTAPI.htmli) is a link to the ServiceNow API documentation.

Connector Setup
---------------

**ServiceNow Instance**: `Your ServiceNow Instance. (eg. https://<Instance>.service-now.com/)`

**Table Name**: `The internal table name of the resource you wish to interact with. (eg. <alm_hardware>)` 

To find the table name, you should navigate to `System Definition > Tables` inside your ServiceNow instance. Please note this is different to the 'Label', which is the human friendly name.

![](./images/ServiceNowTables1.png)

On the next interface, you should enter:

**Username**: `The username of the account which will make the requests to ServiceNow.`

**Password **: `The password for this account.`

After clicking *next*, the connector will be authenticated.

Notes
---------------
If you wish to access multiple tables, you can install the connector again, with the same authentication credentials, but ensure to change the **Table Name** field to the other table you wish to access. It is recommended you name the connector installation based on the table you wish to access.

