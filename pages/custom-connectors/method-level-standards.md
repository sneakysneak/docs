---
title: Method Level Standards
sidebar: cyclr_sidebar
permalink: method-level-standards
tags: [connector-creation]
---
Cyclr Method Level Standards Guide
---------------------------

# Settings
|Setting|Description|
|--- | ---|
|Name|  |
|Description|  |
|Warning|  |
|Status|  |
|Comments|  |
|Category|  |
|Method Type|  |
|Create Webhook Method Type| |
|Delete Webhook Method Type|  |
|Webhook Field Discovery|  |
|Singular WebhookUrl?|  |
|HTTP Method|  |
|Endpoint|  |
|Inbound Paging?|  |
|Inbound Page Size|  |
|Outbound Paging?|  |
|Outbound Page Size|  |
|Outbound Array Location|  |
|Data Type|  |
|XML Root Element|  |
|Hide|  |

# Rate Limits
# Request Format
## Field Handling

|Setting|Description|
|--- | ---|
|Add Field|  |
|Generate Fields|  |
|Delete Selected Fields|  |
|Data Type|  |
|Custom Fields Lookup Method|  |

## Fields
|Setting|Description|
|--- | ---|
|Connector Field|  |
|System Field|  |
|Display Name|  |
|Description|  |
|Hidden|  |
|Optional|  |
|Data Type|  |
|Default Value|  |
|Trigger|  |
|Field Values|  |

# Response Format
## Field Handling

|Setting|Description|
|--- | ---|
|Add Field|  |
|Generate Fields|  |
|Delete Selected Fields|  |
|Data Type|  |
|Time Filter Field|  |
|Custom Fields Lookup Method|  |

## Fields
|Setting|Description|
|--- | ---|
|Connector Field|  |
|System Field|  |
|Display Name|  |
|Description|  |
|Hidden|  |
|Optional|  |
|Data Type|  |
|Default Value|  |
|Trigger|  |
|Field Values|  |

# Parameters
## Parameter Fields

|Field|Description|
|--- | ---|
|Target Type|[Target Types](####target-types)|
|Target Name|Dictates how the parameter will be sent in the request. Must match the API definition.|
|Display Name|The readable equivalent of the target name. Should match Cyclr Standards.|
|Description|Should describe the parameter. If possible use the API description.|
|Trigger|Will give a dropdown of available triggers that can be used as a lookup for the parameter.|
|Hidden|Toggles whether or not a parameter will be shown to the user.|
|Optional|Toggles whether or not a parameter must be included.|
|Parameter Values|  |

## Target Types
|Target Type|Description|
|--- | ---|
|Http Header|  |
|Merge Field|  |
|Query String|  |
|Filter Field|  |
|Response Field|  |
|Script|  |
|Index|  |
