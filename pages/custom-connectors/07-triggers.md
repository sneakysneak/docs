---
title: Connector Triggers
sidebar: cyclr_sidebar
permalink: connector-triggers
tags: [connector-creation]
---

## Triggers

Triggers are used for dynamic lookups. For example, if you want to provide a lookup of 'Acount IDs' you must have already defined a method in the connector to 'list accounts'.  The trigger will then use the method once the connector is authenticated to allow a look up and select.

The settings for an Accounts the Account Id lookup would look something like this

{% raw %}
    "Parameters": [
        {
            "TargetType": "MergeField",
            "TargetName": "AccountId",
            "DisplayName": "Account ID",
            "Description": "User account.",
            "IsOptional": false,
            "TriggerName": "Lookup Account"
        }
    ],
    "Triggers": [
    {
        "Name": "Lookup Account",
        "MethodName": "Get Accounts",
        "IdentifierKey": "[accounts].id",
        "HumanReadableKey": "[accounts].name"
    }
    ]
{% endraw %}

Note that when the user choose **Lookup** for the parameter **AccountId **in Step Setup, Cyclr will use the Lookup Account trigger, call **Get Accounts** and populate a list of accounts.

Triggers need to be defined at the connector level with a unique **Name**. **MethodName **is the method that Cyclr will call to populate parameter values.

**IdentifierKey **is the key value Cyclr will use. **HumanReadableKey **is the display value Cyclr will display in Step Setup.

For example, if a user chooses Account **Example **with ID **1000**, Cyclr will fill the mergefield with **1000**.

The API endpoint becomes:

    "https://example.com/1000/Objects"

[Learn About Custom Connector Scripting ](./scripting)
