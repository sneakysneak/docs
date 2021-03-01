---
title: Github Authentication
sidebar: cyclr_sidebar
permalink: github-authentication
tags: [connector]

---

## Before Starting

You will need to provide your Cyclr Partner 'Service Domain' as part of the process of setting up access so best to have that information to hand before starting. This is specific to your instance of Cyclr and it can be found from the Cyclr Partner Console under:
Settings > General Settings > Service Domain.

Your Cyclr Partner will have been setup with a default Service Domain, but this can be changed if you would prefer to remove mentions of 'Cyclr' from it.
  
## Registering Your Application

Go to your GitHub settings.
Select Applications > Developer applications tab.
Pick an existing application or hit Register new application.
Set a few parameters for your application and get the Client ID and Client Secret.

The callback URL should look like this:  https://{YOUR_SERVICE_DOMAIN}/connector/callback



