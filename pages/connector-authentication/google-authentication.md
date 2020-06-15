---
title: Google Authentication
sidebar: cyclr_sidebar
permalink: google-authentication
tags: [connector]

---

##  Google Partner Setup

Google makes use of OAuth 2.0 for remote API access. You must register Cyclr with Google as your own Project to receive OAuth Client ID and Client Secret values to enable Cyclr to authenticate with Google.

For your reference, here is a link to [Google’s own documentation](https://developers.google.com/identity/protocols/OAuth2WebServer).

## Before Starting

You will need to provide your Cyclr Partner 'Service Domain' as part of the process of setting up access so best to have that information to hand before starting. This is specific to your instance of Cyclr and it can be found from the Cyclr Partner Console under:
Settings > General Settings > Service Domain.

Your Cyclr Partner will have been setup with a default Service Domain, but this can be changed if you would prefer to remove mentions of 'Cyclr' from it.
  
## Registering Your Application

### Create a Project

Sign up for a Google account, or log into your existing account if you have one, then go to the
[Google Developers' Console](https://console.developers.google.com/) to create your Project, and enable the relevant Google APIs.

Step 1 - Click your organisation name at the top to open a popup showing your existing Projects, if any:

![Select Organisation Name](./images/google-auth-1.png)

Step 2 -	Take the option to create a NEW PROJECT in the top right: 

![Create New Project](./images/google-auth-2.png)

*	enter a name for your Project, perhaps the name of your product, and optionally set the Project ID to something other than the suggested value:

![New Project Details](./images/google-auth-3.png)

### Setting up Application Details

From the the **APIs & Services** Dashboard:

Step 1 - Go to Credentials.	(ignore the "Create credentials" button for now as we must first setup the OAuth consent screen)

Step 2 - Choose **OAuth consent screen** along the top - values you enter here will be shown to your users when they authenticate Cyclr's Google Connectors.

Step 4 - set Application Type to Public.

Step 5 -	Enter a suitable name for your application, e.g. "My Product Integrations", upload a logo, set an appropriate email address for your users to get in touch through, should they need to.

Step 5 -	Leave the default Scopes for Google APIs values.

Step 6 -	under Authorised domains add your Cyclr Partner **Service Domain** found in your Cyclr Console under Settings > General Settings.

The Google Console will automatically remove any subdomain part as appropriate, leaving just the top private domain part, e.g. "mysubdomain.cyclr.com" will become "cyclr.com".  You may also see a notice saying "Must be a top private domain" which is just notifying you that it's automatically removed the subdomain part.

Step 7 -	Provide values for the 3 "link" options to enable users to find out more about your organisation/product.

### Creating Google Credentials

From the **APIs & Services** Credentials page:

Step 1 - Click the 'Create Credentials' button and select the option to use 'OAuth client ID'.

![Create Credentials](./images/google-auth-4.png)

Step 2 - The Application Type is 'Web application'.

Step 3 - Enter a Name for the OAuth 2.0 client ID that's being created. This name is only used to identify the client in the console and will not be shown to end users.

Step 4 - Under Authorised redirect URIs add the following (explained earlier in ['Before Starting'](#before-starting)):

*	https://[Your Cyclr Service Domain]/connector/callback

Step 5	- Click the **Create** button, you'll then be presented with your Google Project's OAuth client ID and client secret which you should note for later use:

![OAuth Details](./images/google-auth-5.png)

## Enable Google APIs

Google's services (Sheets, Gmail, Calendar, etc) are offered as separate APIs which you must individually enable within the Google API Console for your Project.

Which APIs you enable depends on which Cyclr Connectors you wish to work with, and some Connectors require more than one Google API to be enabled for them to be fully functional.

For example, the **Google Sheets** Connector requires you to enable the Google Sheets API *and* the Google Drive API.  If you only enable the Google Sheets API, Cyclr will be able to work with data within a Spreadsheet, but it won’t have access to list the available Spreadsheets to choose from.

For each API you require, follow these steps:

Step 1 - From the Google API Console, go to APIs & Services.

Step 2 - On the Dashboard click the +ENABLE APIS AND SERVICES button at the top.

Step 3 - Either enter part of the name of a Google API, “sheets” for example, or scroll to find it.

Step 4 - Click the API's large button when shown.

Step 5 - On the next page click the API's ENABLE button.

*	return to the APIs & Services page.


Below are Cyclr Connectors that require multiple Google APIs to be fully functional:

* Google Sheets - Google Sheets API and Google Drive API


## Additional Setup for Google AdWords

The Google AdWords connector requires [additional setup](https://developers.google.com/adwords/api/docs/guides/signup) before you can access its API.

Step 1 - Sign in or sign up for a Google AdWords manager account

Step 2 - Go to SETUP > AdWords API Centre

Step 3 - Complete the form to create a developer token

Step 4 - Once you have created a developer token, go to Access level > Apply for Basic Access

Step 5 - Submit the Adwords API Token Application

Make a note of your developer token, you will need it when you use Google AdWords methods in Cyclr.


