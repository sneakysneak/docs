---
title: JotForm Connector Guide
sidebar: cyclr_sidebar
permalink: jotform-connector
tags: [connector]
---

## Setup

To authenticate the JotForm connector you will need an API Key, the server your account uses, and the ID of the form you wish to work with.

You will need to install a seperate instance of the connector for each form you wish to work with.

### API Key

To obtain your API Key, within JotForm:

1. Navigate to **(icon in top-right corner) > Settings > API > API KEYS**

2. If there is not already a key present, click 'Create New Key'

3. The permissions should be set to 'Full Access'

### Server

To find out which server your JotForm account uses:

1. Navigate to **(icon in top-right corner) > Settings > Data**

2. If the "Europe Datacenter" box is checked, your account uses the EU server

### Form ID

The Form ID can be found in the URL of the form. For example, if the URL is: **https://<span>www.jotformpro.</span>com/form/30693660548966** the **Form ID is 30693660548966**.

### File Access

In order to download files using the connector you must disable one of the privacy settings in JotForm as follows:

1. Navigate to **(icon in top-right corner) > Settings**

2. Scroll down to the 'Privacy' category of checkboxes

3. Make sure the 'Require log-in to view uploaded files' checkbox is **not selected**

### Connector Setup

1. Locate the JotForm connector

   > Cyclr Console > Connectors > Connector Library > JotForm

2. From the Edit Connector interface click 'Setup'

3. Enter your Form ID

4. For the "Server" field, enter either EU or NON-EU depending on which server your JotForm account uses

5. Click 'Next'

6. Enter your API Key

7. Click 'Next'

The connector is now authenticated and ready to use.
