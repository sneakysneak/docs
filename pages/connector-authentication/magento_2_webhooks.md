---
title: Magento 2 Webhooks Connector
sidebar: cyclr_sidebar
permalink: magento-2-webhooks-connector
tags: [connector]
---

Magento 2 Webhooks Setup
---------------

---
It is assumed that you have already installed our [Magento 2 Webhooks plugin](https://github.com/cyclr/cyclr-magento-2).

---

To authenticate the connector you will need to use your existing Magento 2 API Key.

To find your API key, 

1. Log in to the admin portal, and click `System` > `Extensions` > `Integrations`.
2. Click the `Edit` pencil next to your integration.

![](./images/edit_integration.png)

3. Scroll down and copy your access token

![](./images/integration-tokens.png)

Now that you have your Access token go to the `Connector Setup` page in Cyclr.

1. On the first page you should enter the domain of your Magento site e.g. `https://my-magento-site.com` and click `Next`.
2. Paste your `Access Token` into the `API Key` field and click `Next`.
3. Your connector is now setup and ready to go.

### Available Webhooks

* Customer
    * New Customer
    * Customer Updated
    * Customer Deleted
* Product
    * New Product
    * Product Updated
    * Product Deleted
* Order
    * New Order
    * Order Updated
* Subscriber
    * Subscriber Saved



