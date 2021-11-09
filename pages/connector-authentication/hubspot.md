---
title: HubSpot Connector Guide
sidebar: cyclr_sidebar
permalink: hubspot-connector
tags: [connector]
---

### HubSpot Setup

For Cyclr to connect with the HubSpot API you will need to create an "App" within HubSpot, as detailed below:

  > Note: This part can be completed once, by a Cyclr Partner.  The client/customer does not need their own separate App within HubSpot.

1. Login to the HubSpot Developer Portal [here](https://app.hubspot.com/signup-v2/developers)
2. Follow the HubSpot [documentation](https://developers.hubspot.com/docs/faq/how-do-i-create-an-app-in-hubspot) to create an application
3. In the `Auth` tab you will see a `Client ID` and `Client Secret`.  Make a note of these to use in Cyclr's Connector setup.
4. The Redirect URL that creates the link between your Cyclr Console and HubSpot is shown on the page where the Client ID and Client Secret are entered.  It has the form
`https://[Your Cyclr Service Domain]/connector/callback`
5. It's not necessary to set Scopes at this point - see next section for details on this.

### Scopes

As mentioned above - it's not necessary to set scopes at this point. The default scopes of `crm.objects.contacts.read`,`crm.objects.deals.read` and `crm.objects.companies.read` will be requested by the Cyclr Connector (along with any other scopes you choose to set within your Cyclr Console).

#### IMPORTANT NOTE (November 2021)
The way that HubSpot handles contact scopes has recently changed:

[https://developers.hubspot.com/docs/api/oauth/contacts-scope-migration](https://developers.hubspot.com/docs/api/oauth/contacts-scope-migration)

This should not affect you if you have set up a new HubSpot App, but contact Cyclr Support if you have any questions.

If you have an _existing_ HubSpot app this is likely to have been auto-migrated by HubSpot in early November 2021.  This shouldn't affect your integrations, but we'd recommend upgrading your Account Connector to the latest version at your earliest opportunity.


### Permissions

In order to use the Products and Line Items methods, the user must be assigned a [paid Sales Hub seat](https://knowledge.hubspot.com/articles/kcs_article/account/manage-sales-hub-and-service-hub-paid-users) within HubSpot.

### Connector Setup

The Connector now can be installed using the credentials obtained in the above steps:

**Client ID**: `Client ID`

**Secret**: `Client Secret`

**Scopes/Optional**: This defines what permissions will be requested on the consent screen presented to your users.  

By default, all users will be asked to consent to the following permissions/scopes `crm.objects.contacts.read`,`crm.objects.deals.read` and `crm.objects.companies.read`, and where appropriate (these are optional scopes, in other words) users will be asked to consent to ``content`` ``reports`` ``e-commerce`` ``forms``.

Should you need to request *alternative* scopes/optional scopes, this is where you would set them.

You will then be prompted to log in, select your HubSpot and authorize access to the connector.

### Account Selection

When authenticating the HubSpot Connector and signing into HubSpot, the user will be presented with the HubSpot **Choose an Account** screen.

During testing, you should select your main HubSpot account, rather than your developer account.  You can identify the main account by looking for the one with items shown under the "PRODUCTS" heading as shown below.

In this example, that would be the "Cyclr" account:

![](./images/hubspot-choose-acct.png)

### Connector Parameters 

Useful if accessing this Connector via the API.  Property Names given here are in the same format as they should be passed to the API.

| Property Name   | Description    |
| ----------- | -----------    |
| Scopes      | The scopes of the connector. Default value is `crm.objects.contacts.read`,`crm.objects.deals.read`,`crm.objects.companies.read`. |
| OptionalScopes   | The optional scopes of the connector. Default value is "content reports e-commerce forms" |
