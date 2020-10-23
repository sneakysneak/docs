---
title: Oracle NetSuite - SuiteTalk REST Web Services Connector Guide
sidebar: cyclr_sidebar
permalink: netsuite-suitetalk-rest-connector
tags: [connector]
---

The Oracle NetSuite - SuiteTalk REST Web Services connector is authenticated with the OAuth2.0 protocol. You will need to register an application and provide the connector with that application's Client ID, Client Secret and your Account ID.

## NetSuite Setup

Firstly [log in](https://system.netsuite.com/pages/customerlogin.jsp) to your NetSuite account.

### Creating An App

1. From the top navigation bar go to **Setup** > **Integration** > **Manage Integrations** > **New**

2. Enter a name for the app

3. "State" should be "Enabled"

4. From the Authentication section select **OAuth2.0**, enter your Redirect URI and select the scope **REST WEB SERVICES**

   > Redirect URI should be {% raw %}https://{{Your Cyclr service domain e.g. app-h.cyclr.com}}/connector/callback{% endraw %}

5. Make sure that neither **Token-based Authentication** or **User Credentials** are selected

6. Scroll down and click **Save**

You will be presented with your Client ID and Client Secret. Make a note of these as they will only be shown once.

### Finding Your Account ID

1. From the top navigation bar go to **Setup** > **Company** > **Company Information**

![Company information](./images/netsuite_suitetalk_1.png)

### Enable OAuth2.0 For Your Account

1. From the top navigation bar go to **Setup** > **Company** > **Enable Features**

2. Click the **SuiteCloud** subtab

   ![SuiteCloud tab](./images/netsuite_suitetalk_2.png)

3. In the **SuiteScript** section check **Client SuiteScript** and **Server SuiteScript**

4. In the **SuiteTalk (Web Services)** section make sure **REST Web Services**, **REST Record Service (Beta)** and **REST Query Service (Beta)** are checked

5. In the **Manage Authentication** section check **OAuth 2.0**

6. Scroll to the bottom of the page and click **Save**

## Connector Setup

1. Locate the Oracle NetSuite - SuiteTalk REST Web Services connector

   > Cyclr Console > Connectors > Connector Library > Oracle NetSuite - SuiteTalk REST Web Services

2. From the Edit Connector interface click 'Setup'

3. Enter your Client ID, Client Secret and Account ID

4. Click **Next**

5. Click **Sign In**

6. A new window will open prompting you to log in to your NetSuite account

7. You will be presented with the message "The application is requesting permission to access..."

8. Click **Continue**

You should now have been redirected to Cyclr which means that the connector is authenticated and ready to use.

## User Guide

### Query Parameter

Several methods have an optional **Query** parameter. Each condition consists of a field name, an operator, and a value. You can join several conditions using the AND / OR logical operators, and you can use () to mark precedence.

The following table contains the list of available query operators with their associated field types.

| Field Type                               | Allowed Operators                                                                                                                                                                               |
| :--------------------------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| None                                     | EMPTY, EMPTY_NOT                                                                                                                                                                               |
| Boolean                                  | IS, IS_NOT                                                                                                                                                                                     |
| Double, Integer, Float, Number, Duration | ANY_OF, ANY_OF_NOT, BETWEEN, BETWEEN_NOT, EQUAL, EQUAL_NOT, GREATER, GREATER_NOT, GREATER_OR_EQUAL, GREATER_OR_EQUAL_NOT, LESS, LESS_NOT, LESS_OR_EQUAL, LESS_OR_EQUAL_NOT, WITHIN, WITHIN_NOT |
| String                                   | CONTAIN, CONTAIN_NOT, IS, IS_NOT, START_WITH, START_WITH_NOT, END_WITH, END_WITH_NOT                                                                                                           |
| Date / Time                              | AFTER, AFTER_NOT, BEFORE, BEFORE_NOT, ON, ON_NOT, ON_OR_AFTER, ON_OR_AFTER_NOT, ON_OR_BEFORE, ON_OR_BEFORE_NOT                                                                                 |

Not all operators accept one value. Some operators do not require any value, some operators require two values, and some operators accept any number of values. Consider the following examples:

- Unary operators: The EMPTY and EMPTY_NOT operators do not accept any values. For example: **companyName EMPTY**
- Ternary operators: The BETWEEN, BETWEEN_NOT, WITHIN, and WITHIN_NOT operators accept two values. For example: **id BETWEEN_NOT [1, 42]**
- N-ary operators: The ANY_OF and ANY_OF_NOT operators do accept one or any higher number of values. For example: **id ANY_OF [1, 2, 3, 4, 5]**

Example:

If you wanted to filter customers by email addresses starting with "barbara" you would enter the query **email START_WITH barbara**, which would result in the following request being made:

```sh
GET https://demo123.suitetalk.api.netsuite.com/services/rest/record/v1/customer?q=email START_WITH barbara
```
