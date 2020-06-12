---
title: Google Authentication V2
sidebar: cyclr_sidebar
permalink: google-connector-V2
tags: [connector]

---

##  Google Partner Setup

Google makes use of OAuth 2.0 for remote API access. You must register Cyclr with Google as your own Project to receive OAuth Client ID and Client Secret values to enable Cyclr to authenticate with Google.
For your reference, Google’s own documentation for creating a Project and Credentials can be found [here](https://developers.google.com/identity/protocols/OAuth2WebServer).

## Registering Your Application

### Introduction

Sign up for a Google account, or log into your existing account if you have one, then go to the
[Google API Console:https://console.developers.google.com/] to create your Project and enable the relevant Google APIs.
Create your Project in the Google API Console

1.	click your organisation name at the top to open a popup showing your existing Projects, if any:

IMAGE 1

2.	click NEW PROJECT in the top right: 

IMAGE 2

3.	enter a name for your Project, perhaps the name of your product, and optionally set the Project ID to something other than the suggested value:

IMAGE 3

4. you'll be returned to the APIs & Services Dashboard.
5. go to Credentials.	(ignore the "Create credentials" button for now as we must first setup the OAuth consent screen)
6. choose OAuth consent screen along the top - values you enter here will be shown to your users when they authenticate Cyclr's Google Connectors.
a	set Application Type to Public.
b	enter a suitable name for your application, e.g. "My Product Integrations", upload a logo, set an appropriate email address for your users to get in touch through, should they need to.
c	leave the default Scopes for Google APIs values.
d	under Authorised domains add your Cyclr Partner Service Domain found in your Cyclr Console under Settings > Integration Settings.
The Google Console will automatically remove any subdomain part as appropriate, leaving just the top private domain part, e.g. "mysubdomain.cyclr.com" will become "cyclr.com".  You may also see a notice saying "Must be a top private domain" which is just notifying you that it's automatically removed the subdomain part.
e	provide values for the 3 "link" options to enable users to find out more about your organisation/product.
f	click Save and you'll be returned to the Credentials page. 

## Creating Google Credentials

From the APIs & Services Credentials page:
•	click the Create credentials button and select OAuth client ID:

IMAGE 4

•	choose an Application Type of Web application.
•	enter a Name for the OAuth client ID that's being created.
•	under Authorised redirect URIs add the following:
o	https://my.cyclr.com/connector/callback
(change .com to .uk if your Cyclr Console is located at the .uk domain)
o	https://[Your Cyclr Service Domain e.g. app-h.cyclr.com]/connector/callback
(your Cyclr Partner Service Domain found in your Cyclr Console under Settings > Integration Settings.)
•	click the Create button, you'll then be presented with your Google Project's OAuth client ID and client secret which you should record for later use:

IMAGE 5

## Enable Google APIs

Google’s services (Sheets, Gmail, Calendar, etc) are offered as separate APIs which you must individually enable within your Google API Console for your Project.

Which APIs you enable depends on which Cyclr Connectors you wish to work with, and some Connectors require more than one Google API to be enabled for them to be fully functional.  For example, the Google Sheets Connector requires you to enable the Google Sheets API and the Google Drive API.  If you only enable the Google Sheets API, Cyclr will be able to work with data within a Spreadsheet, but it won’t have access to list the available Spreadsheets to choose from.

For each API you require, follow these steps:
•	from the Google API Console, go to APIs & Services.
•	on the Dashboard click the +ENABLE APIS AND SERVICES button at the top.
•	either enter part of the name of a Google API, “sheets” for example, or scroll to find it.
•	click the API's large button when shown.
•	on the next page click the API’s ENABLE button.
•	return to the APIs & Services page.

List of Cyclr Connectors that require multiple Google APIs to be fully functional:
Google Sheets: Google Sheets API and Google Drive API

