---
title: Console Data Retention Settings
sidebar: cyclr_sidebar
permalink: console-data-retention-settings
tags: [managing-cyclr]

---
 
## Data Retention 

The data retention settings allow you to specify how long both successful transactions and transaction errors should be retained.
 
By default both are set to retain data to thirty days.
 
Retention for Successful Transactions and Errored Transactions can be turned off, and adjusted independently of each other, and the retention period can be set in Hours, Days, or Weeks.
 
## OAuth Client Credentials

### Password Grant Client ID

The Password Grant is no longer the recommended way to authenticate API requests. As such this will be deprecated in the future. However accounts which had Password Grant Client IDs set up will still be able to access and refresh them here.
For more details on why this is no longer recommended please see https://oauth.net/2/grant-types/password/.
 
### Client Credentials

The Client ID is used to authenticate calls to the Cyclr API. 
Here you're abel to generate up to 5 unique pairs of Client IDs and Secrets. Client credentials can also be revoked here.
 
### Access Tokens

The access token represents the authorization of a specific application to access specific parts of a user’s data.
This section lists each time an Access Token has been generated for use with the API along with the Client ID which was used to generate it, the account by which it was generated, the expiry date, and the ability to revoke active access tokens.
 
## Console Administrators

Console Administrators have access to both the Cyclr Console and Cyclr Partner API.
The Console Administrators page is where you can invite or remove people as console administrators, as well as enabling or disabling Account Activity and Billing notifications on a individual basis.
 
## IP Restrictions

### API and Console
Access to the API and Console can both be edited here by white-listing approved IP addresses of your organisation. By default there is no IP restriction, however if edited only the IP addresses present will be able to access the API or Console.
 
### API - Call Non-Native Connector Methods
APIs for calling non-native (standard) connector methods are blocked by default, and can only be changed on request to the Cyclr support 

