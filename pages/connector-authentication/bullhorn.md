---
title: Bullhorn Authentication
sidebar: cyclr_sidebar
permalink: bullhorn-connector
tags: [connector]
---

# Bullhorn

## Partner Setup

Bullhorn uses OAuth 2 for API access.

## FAQ

### Apache Tomcat Error

After you are redirected to Bullhorn during the authentication process, sometimes Bullhorn display an Apache Tomcat error like this:

![Bullhorn Redirect Error](./images/bullhorn-redirect-error.png)

This is a known issue with Bullhorn. The solution is to clear the Bullhorn cookies in your browser, or open Cyclr and authenticate the connector in a private window.