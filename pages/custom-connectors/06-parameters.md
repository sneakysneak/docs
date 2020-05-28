---
title: Connector Parameters
sidebar: cyclr_sidebar
permalink: connector-parameters
tags: [connector-creation]
---

## Parameters

Parameters are used to define a range of HTTP fields, e.g. HTTP headers, mergefields, query string parameters, etc.

You can define parameters at the connector level or method level. If a parameter is defined at the connector level, it will be global for all methods in the connector.

For example:
{% raw %}
    "Parameters": [
        {
            "TargetType": "QueryString",
            "TargetName": "before_created_date",
            "DisplayName": "Before Created Date",
            "Description": "Restrict the response to objects created before the date.",
            "IsOptional": true
        }
    ]
{% endraw %}

The **before_created_date** can then be used to filter objects to a specific range. Cyclr users will see this parameter in Step Setup.

Parameters can be defined in conjunction with URL endpoint mergefields, for example, if your URL looks like:

    "Endpoint": "https://example.com/{% raw %}{{AccountID}}{% endraw %}/objects",

Then you can specify **AccountID **as a mergefield parameter:
{% raw %}
    "Parameters": [
        {
            "TargetType": "MergeField",
            "TargetName": "AccountId",
            "DisplayName": "Account ID",
            "Description": "User account.",
            "IsOptional": false
        }
    ]
{% endraw %}

## Parameter Definition

| Property | Description | Recommended Standards |
| --- | --- | --- |
| TargetType |*   HttpHeader: HTTP header *   MergeField: Endpoint mergefield *   QueryString: Query string parameter *   FilterField: Cyclr filter field (can set a date field as FilterField to filter new objects) *   ResponseField: Response field | | 
| TargetName | The name for the parameter.| |
| DisplayName | Display name for the parameter.| |
| Description | Description for the parameter.| |
| TriggerName | Trigger name for the parameter. If you want to dynamically show a list of parameter values for the user to choose from, set `TriggerName` as the trigger you want Cyclr to call. Please see the _Triggers_ section for details.| |
| IsOptional | Set the parameter to be optional or required. The default is required (false).| |
| Hide | Hide the parameter from the user interface. You can use this to hide internal parameters you want to send to the endpoint.| |
