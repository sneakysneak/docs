---
title: Marketo Connector Guide
sidebar: cyclr_sidebar
permalink: marketo-connector
tags: [connector]
---

## Bulk Import/Export

The ability to import and export csv (comma separated values), tsv (tab separated values) or ssv (space separated values) files is supported with methods from the **Bulk Imports** and **Bulk Exports** categories.

### Import

If you haven't done so already, export your data in the chosen format.

For example, if your data is in a Google Sheets spreadsheet and you want to save that as a csv file:

![marketo spreadsheet](./images/marketo_import_1.png)

![marketo save as csv](./images/marketo_import_2.png)

Open this file in a text editor such as Notepad, Visual Studio Code etc.

![marketo csv raw](./images/marketo_import_3.png)

Using the method Create Import Job:

1. Select the File Format (CSV, TSV or SSV)

2. Copy and paste the contents of your file into the File parameter (File parameter > Type a Value > paste the contents)

![create import job configuration](./images/marketo_import_4.png)

The status of the created import job can be checked with the method **Get Import Job Status**. Simply pass it the import job's batch ID

### Export

To export a file (CSV, TSV or SSV) you must:

1. Select the **Create Export Job** method that suits your requirements (Activities, Leads, New Activities or New Leads)

   ![create export job methods](./images/marketo_export_1.png)

2. Define the fields the export file should include (eg. firstName, lastName, email)

3. Optionally select the file format (if not selected this will default to CSV)

   ![create export job configuration](./images/marketo_export_2.png)

4. The response from this method will include the status and the Export ID for use in subsequent methods

   ![create export job response](./images/marketo_export_3.png)

5. Add the created export job to the processing queue with the method **Enqueue Export Job**. Select the Export Type (leads or activities) and enter the Export ID

   ![enqueque export job method](./images/marketo_export_4.png)

6. The export job will now have a status of 'Queued'

7. To check the changing status of the Export Job use the method **Get Export Job Status**, again providing the Export Type and Export ID

8. When the Export Job's status has changed to 'Completed' the file is ready to download using the method **Get Export File**, again providing the Export Type and Export ID

9. **Get Export File**'s response will provide a 'Download' button. Click this to download the file to your system

   ![get export file response](./images/marketo_export_5.png)
   
   
## Authentication

To get a **client ID** and **client secret** you must login to your Marketo installation as an admin.

1. Go to **Admin** > **LaunchPoint** under the **Integration** menu.
2. Click on **View Details** under the service that you want to use. If no services are shown, create a new one.
3. Copy the **client ID** and **client secret** from the prompt.

### Cyclr Setup

Setup your Marketo App within Cyclr:

*   Go to your **Cyclr Console**
*   Click the **Connectors** menu along the top
*   Choose Connector Library
*   Scroll down to **Marketo**
*   Click the **Setup** button

Enter the following values:

**Client ID**:  Enter the client ID that we retrieved from LaunchPoint.

**Client Secret**:  Enter the client secret that we retrieved from LaunchPoint.

**API Subdomain**: The subdomain from your api instance endpoint. For example, "https://{{subdomain}}.mktorest.com". 


Your Marketo Connector is now setup! You can test it by installing it in one of your Cyclr accounts and executing one of the methods to confirm it can return some data.

