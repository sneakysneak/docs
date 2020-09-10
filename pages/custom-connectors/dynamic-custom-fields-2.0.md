---
title: Dynamic Custom Fields
sidebar: cyclr_sidebar
permalink: dynamic-custom-fields-2.0
tags: [connector-creation]
---

Adding Custom Fields Dynamically
----------------------------------

Cyclr can add custom fields dynamically to an authenticated connector, removing the need to add them manually for each installation.

There are two ways to do this:

1. If the API you are accessing has methods for retrieving object metadata, these can be used to define the fields.  <br>See [Enhanced Dynamic Custom Fields](#Enhanced).
2. If the API does not have such methods, Cyclr can parse an example response from an existing method. <br>See [Basic Dynamic Custom Fields](#Basic).

<a name="Enhanced">1. Enhanced Dynamic Custom Fields</a>
----------------------
####Setup:
1. Identify the method within the API that will return the metadata for your object.  You will then need to [create this method within the connector](./connector-methods).
2. The response for this method should be an array, and each item in the array must represent a single field in the object, for example:
```json
{
  "fields": [
    {
      "field_name": "CustName",
      "label": "Customer Name",
      "optional": false
    },
    {
      "field_name": "customfield_bankingid",
      "label":"Banking ID",
      "optional": true
    }
  ]
}
```
3. In the response of the method, set the System Fields to match [the table below](#systemfields), so that Cyclr can access the various parts of each field description.  In the above example, the mappings would look like this:

![](./images/basic-mappings.png)

4. If you are mapping **data types** from the object description, you will need to add some scripting to the method.  This will vary depending on the structure of your method response, but as an example:
```json
// Example method response
{
  "fields": [
    {
      "field_name": "customfield_bankingid",
      "label":"Banking ID",
      "optional": true,
      "data_type": "string"
    }
  ]
}
```
```javascript
// Example method-level script

function after_action(){
  // Check for a response
  if(method_response == null)
  return;
  // Check response contains fields
  if(method_response.fields == null)
  return;
  // Remap fields to values that Cyclr will understand
  for(var i=0;i<method_response.fields.length;i++){
    method_response.fields[i].data_type = select_dt(method_response.fields[i].data_type);
  }
  return true;
}

function select_dt(item){
  /* The case values here will need to be changed to the values returned by your method, so
   instead of "string" it might be "str", and instead of "integer" it might be "int32".*/
  switch(item) {
  case "string":
    return 1;
    break;
  case "integer":
    return 2;
    break;
  default:
    return 1;
  }
}
```

5. You should now update the response fields, to look similar to this example:
![](./images/basic-mappings-with-dt.png)

6. Ensure that the **For Enhanced Custom Fields** option has been checked:
![](./images/for-enhanced-custom-fields.png)

7. Now all you need to do is go to the method where you want to pick up custom fields, and select this method from the **Custom Fields Lookup Method** dropdown menu.  You can do this for the Request, the Response, or both as required:

![](./images/dynamic_custom_fields_image_2.png)

8. Cyclr should now automatically map any custom fields for this method once it is installed.

####<a name="systemfields">Table of System Fields</a>
System Field | Description
--- | ---
cyclr_field_location | Location of the custom field, e.g. [items].custom_field
cyclr_data_type | The data type of the custom field:<br>0=Not Defined. <br>1=Text.<br>2=Integer.<br>3=Float.<br>4=Boolean.<br>5=Date Time.
cyclr_data_type_format | Custom data type format for the custom field
cyclr_default_value | The default value to use for the custom field
cyclr_description | The description of the custom field
cyclr_display_name | The name to display the custom field as
cyclr_is_optional | Indicates if the custom field is optional when part of a request
cyclr_is_readonly | Indicates if the custom field is read-only, if it is it won't be added to any requests

<a name="Basic">2. Basic Dynamic Custom Fields</a>
----------------------
####Setup:
1. Select a method which is able to be called without any field or parameter values being set.  This will be your "Source" method.
2. The response of this method should be in the same structure as your "Target" method (the method for which Cyclr will dynamically map custom fields).

```json
// Example:
// Source method "List All Orders" response
{
  "orders": [
    {
      "id": 1,
      "name": "John",
      "added": "2020-01-01",
      "customfield1": "abcd"
    }
  ]
}

// Target method "List New Orders" Response
{
  "orders": [
    {
      "id": 29,
      "name": "Dave",
      "added": "2020-09-09",
      "customfield1": "wxyz"
    }
  ]
}
```
3. Now all you need to do is go to the method where you want to pick up custom fields, and select this method from the **Custom Fields Lookup Method** dropdown menu.  You can do this for the Request, the Response, or both as required:

![](./images/dynamic_custom_fields_image_1.png)

Cyclr will then attempt to determine the correct Display Name and Data Type of the fields found in the response object.

For more control of the custom fields generated you will need to make use of [Enhanced Dynamic Custom Fields](#Enhanced).
