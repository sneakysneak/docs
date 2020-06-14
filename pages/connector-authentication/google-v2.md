---
title: Google Authentication V2
sidebar: cyclr_sidebar
permalink: google-connector-V2
tags: [connector]

---

##  Google Partner Setup

Google makes use of OAuth 2.0 for remote API access. You must register Cyclr with Google as your own Project to receive OAuth Client ID and Client Secret values to enable Cyclr to authenticate with Google.

For your reference, Google’s own documentation for [Creating a Project and Credentials](https://https://console.cloud.google.com/).

## Registering Your Application

### Create a Project

Sign up for a Google account, or log into your existing account if you have one, then go to the
[Google Cloud Platform](https://console.developers.google.com/) to create your Project, and enable the relevant Google APIs.

*	click your organisation name at the top to open a popup showing your existing Projects, if any:

![](./images/google-auth-1.png)

*	click NEW PROJECT in the top right: 

![](./images/google-auth-2.png)

*	enter a name for your Project, perhaps the name of your product, and optionally set the Project ID to something other than the suggested value:

![](./images/google-auth-3.png)

### Setting up Application Details

* you'll be returned to the APIs & Services Dashboard.

* go to Credentials.	(ignore the "Create credentials" button for now as we must first setup the OAuth consent screen)

* choose OAuth consent screen along the top - values you enter here will be shown to your users when they authenticate Cyclr's Google Connectors.

-	set Application Type to Public.

-	enter a suitable name for your application, e.g. "My Product Integrations", upload a logo, set an appropriate email address for your users to get in touch through, should they need to.

-	leave the default Scopes for Google APIs values.

-	under Authorised domains add your Cyclr Partner Service Domain found in your Cyclr Console under Settings > Integration Settings.
The Google Console will automatically remove any subdomain part as appropriate, leaving just the top private domain part, e.g. "mysubdomain.cyclr.com" will become "cyclr.com".  You may also see a notice saying "Must be a top private domain" which is just notifying you that it's automatically removed the subdomain part.

-	provide values for the 3 "link" options to enable users to find out more about your organisation/product.

### Creating Google Credentials

From the APIs & Services Credentials page:

Step 1 - Take the 'Create Credentials' button and the select the option to use 'OAuth client ID'.

![](./images/google-auth-4.png)

Step 2 - The Application Type is 'Web application'.

Step 3 - Enter a Name for the OAuth 2.0 client ID that's being created. This name is only used to identify the client in the console and will not be shown to end users.

Step 4 - Under Authorised redirect URIs add the following:

*	https://my.cyclr.com/connector/callback
(change .com to .uk if your Cyclr Console is located at the .uk domain)

*	https://[Your Cyclr Service Domain e.g. app-h.cyclr.com]/connector/callback
(your Cyclr Partner Service Domain found in your Cyclr Console under Settings > Integration Settings.)

Step 5	click the Create button, you'll then be presented with your Google Project's OAuth client ID and client secret which you should record for later use:

![](./images/google-auth-5.png)

## Enable Google APIs

Google’s services (Sheets, Gmail, Calendar, etc) are offered as separate APIs which you must individually enable within your Google API Console for your Project.

Which APIs you enable depends on which Cyclr Connectors you wish to work with, and some Connectors require more than one Google API to be enabled for them to be fully functional.  For example, the Google Sheets Connector requires you to enable the Google Sheets API and the Google Drive API.  If you only enable the Google Sheets API, Cyclr will be able to work with data within a Spreadsheet, but it won’t have access to list the available Spreadsheets to choose from.

For each API you require, follow these steps:

*	from the Google API Console, go to APIs & Services.

*	on the Dashboard click the +ENABLE APIS AND SERVICES button at the top.

*	either enter part of the name of a Google API, “sheets” for example, or scroll to find it.

*	click the API's large button when shown.

*	on the next page click the API’s ENABLE button.

*	return to the APIs & Services page.

List of Cyclr Connectors that require multiple Google APIs to be fully functional:
Google Sheets: Google Sheets API and Google Drive API

Setting Google OAuth values in Cyclr
Now you have a client ID and client secret, you can set these back in Cyclr.

*	go to your Cyclr Console.

*	click the Connectors menu then Connector Library.

*	find the Google Connector you wish to use.

*	click its Setup button.

*	enter your client ID and client secret values.

*	click Save Changes.

Additional Setup for Google AdWords
The Google AdWords connector requires [additional setup:https://developers.google.com/adwords/api/docs/guides/signup] before you can access its API.

*	Sign in or sign up for a Google AdWords manager account

*	Go to SETUP > AdWords API Centre

*	Complete the form to create a developer token

*	Once you have created a developer token, go to Access level > Apply for Basic Access

*	Submit the Adwords API Token Application

Make a note of your developer token, you will need it when you use Google AdWords methods in Cyclr.


