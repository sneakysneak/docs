---
title: Custom Service Domain
sidebar: cyclr_sidebar
permalink: custom-domains
tags: [installing, embedding, service domain]
---

### Using your own domain as a Cyclr Service Domain

To use your own domain as Cyclr Service Domain, follow these steps:

* You must provide us with an SSL certificate for the domain you wish to use with Cyclr, e.g. ```integration.mydomain.com```.
* You must create a CNAME DNS record pointing ```integration.mydomain.com``` to the Cyclr Instance you're hosted on. If you're on the US Instance for example, that will be `my.cyclr.com`.
* Contact Cyclr Support once the above tasks have been completed and we'll perform some setup on your Cyclr Console.
* You will need to provide details of a new SSL certificate before the existing one expires (we plan to make this less manual in future).


### Reasons to do this

Due to how web browsers handle third party cookies, you should setup a custom domain if you are displaying Cyclr through an iframe in your own web application.

It should be a subdomain of the domain your web application is hosted at.

Without this, your users may experience issues where the page isn't displayed by their web browser such as when using the Safari browser or Chrome Incognito windows.
