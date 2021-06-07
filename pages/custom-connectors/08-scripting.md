---
title: Connector Scripting
sidebar: cyclr_sidebar
permalink: connector-scripting
keywords: action_data
redirect_from: "/custom-connector-scripting/"
tags: [connector-creation]
---

Cyclr supports Javascript as its scripting language, allowing you to manipulate data before it's sent as well as after it's been retrieved.  This can be useful when moving data between applications as what's valid in one, may not be valid in another.  Also, sometimes data just doesn't quite "fit".

Script can be used when building a Connector and on Steps in a Template or Cycle.

If you're working on a Cycle in the Builder and need to perform a change to some data, click the Step Setup button on a Step then either use Inline Script in a Mapping for something simple, or expand the Advanced Settings area and enter some Script to tie in to Cyclr's [Events](https://docs.cyclr.com/custom-connector-scripting#events) as described below.

For Inline Script, you must prefix the Javascript code with "=" (an equals sign), e.g.:
```javascript
=(100 * 2)
```
or
```javascript
=`[Mergefield]` === '' ? 'no value' : `[Mergefield]`;
```

It's best to use ` characters (backticks) around string values being merged in as that will prevent carriage returns and any quote characters from breaking your Script.

*Note: [Mergefield] above represents fields inserted by Cyclr in **Step Setup** when choosing **Type a Value** and selecting from the dropdowns.*

## Events

Events are triggered at certain points when a Cycle runs, allowing you to modify data using "event handlers" which are simply Javascript functions.

### Event Handlers

To add an event handler, put a Javascript function at the Connector or Method level, or in the Advanced Settings area of a Step in the Cycle Builder, using the event name as the name of the function, e.g.:

```javascript
function before_action() {
    /* Handle event here */
    return true;
}
```

Event handlers entered at the Connector level will be called for all of its Methods.  Event handlers entered at the Method level will only be called for that Method.

If you need to pass a value from a **before_action** handler to an **after_action** handler and you're not able to put it in the **method_request** object as part of the Request (the API being called might object to it), you can use the **method_request_mergefields** object as it's persisted across those two events. The **script_parameters** object, for example, is not persisted across any events.

### Event Handler Order

If an event handler exists at more than one level for the same event, i.e. Connector level as well as Method level, all of those event handlers are called.

This is useful if common processing of the data is required across all Methods using a Connector level **after_action** handler, but some Methods need further processing so an additional Method level **after_action** handler can also be used.

The order that Cyclr calls handlers for the same event is as follows:

Events beginning with "**before**" (such as before_action):

	Method -> Connector -> Builder Step

All other events (such as after_action):

	Connector -> Method -> Builder Step


### Global Objects
<br>
method_response_fields: Array containing a Method's Response Fields.


### Events

(click to expand)

<details>
  <summary><b>+ before_webhook</b></summary>

<h4>Description</h4>
Called when a webook request has been received and before anything else is done. Method is used to decide if the request should be continued or return a custom message to the caller.

<hr>

<h4>Global objects available to event</h4>
<br>
<code>method_endpoint</code>: The webhook request URL<br>
<code>method_request_headers</code>: The webhook request headers<br>
<code>method_request</code>: The webhook request body<br>
<code>method_request_parameters</code>: The webhook request parameters<br>
<code>method_response_headers</code>: The response headers for the request<br>
<code>method_response</code>: The response body for the request<br>
<code>return</code>: true for the webhook to continue normal execution, false to stop execution of the request and send the response body/headers to the caller
<hr>
</details>

<details>
<summary><b>+ after_webhook</b></summary>

<h4>Description</h4>

Called immediately after a Request to a Webook has been received, whether the Cycle is currently running or stopped.
<hr>

<h4>Global objects available to event</h4>

<code>method_response</code>: object that was POSTed to the Cyclr webhook<br>
<code>cycle_variables</code>: Allows access to Cycle variables.  Changes are not persisted.<br>
<code>cycle_step_id</code>: ID of the step that is executing the script.<br>
<code>cycle_id</code>: The ID of the cycle the script is running in<br>
<code>cyclr_account_id</code>: The internal ID of the account the script is running in<br>
<code>external_account_id</code>: The external ID of the account the script is running in<br>
<code>return</code>: true for the webhook to continue normal execution, false to ignore the webhook request
<hr>
</details>

<details>
<summary><b>+ before_action</b></summary>

<h4>Description</h4>

Called before Cyclr makes a request to an external API.

If a Method uses Paging, this function is called before each page is retrieved.

<hr>

<h4>Global objects available to event</h4>

<code>method_request_headers</code>: HTTP headers for the request<br>
<code>method_request_parameters</code>: Querystring parameters for the request<br>
<code>method_request</code>: Object that will be posted to the third party API<br>
<code>method_request_mergefields</code>: Mergefields for the request<br>
<code>cycle_variables</code>: Allows access to Cycle variables.  Changes are not persisted.<br>
<code>cycle_step_id</code>: ID of the step that is executing the script.<br>
<code>cycle_id</code>: The ID of the cycle the script is running in<br>
<code>cyclr_account_id</code>: The internal ID of the account the script is running in<br>
<code>external_account_id</code>: The external ID of the account the script is running in<br>
<code>action_data</code>: An object used to persist data between some event handler functions, allowing data to be passed between them.  Accessible in before_action, after_action, after_action_paging, action_condition and after_error.<br>
<code>return</code>: true to continue with the request to the third party API, false to abort the request (use throw for a more useful step error message)
<hr>
</details>

<details>
<summary><b>+ after_action</b></summary>

<h4>Description</h4>

Function is called when Cyclr has a response from an external API.

If a Method uses Paging, this function is called after each page is retrieved.

<hr>

<h4>Global objects available to event</h4>

<code>method_endpoint</code>: The URL of the original request<br>
<code>method_request</code>: object that was posted to the third party API<br>
<code>method_request_mergefields</code>: mergefields for the request<br>
<code>method_response_headers</code>: The response headers for the request<br>
<code>method_response</code> object that was received from the third party API.  If the Method uses paging, this contains only the current page's Response.<br>
<code>cycle_variables</code>: Allows access to Cycle variables.  Changes are not persisted.<br>
<code>cycle_step_id</code>: ID of the step that is executing the script.<br>
<code>cycle_id</code>: The ID of the cycle the script is running in<br>
<code>cyclr_account_id</code>: The internal ID of the account the script is running in<br>
<code>external_account_id</code>: The external ID of the account the script is running in<br>
<code>action_data</code>: An object used to persist data between some event handler functions, allowing data to be passed between them.  Accessible in before_action, after_action, after_action_paging, action_condition and after_error.<br>
<code>return</code>: true
<hr>
</details>

<details>
<summary><b>+ after_action_paging</b></summary>

<h4>Description</h4>

If this function is provided, it is called once after all pages of data have been retrieved, whether Paging has been implemented or not.

<hr>

<h4>Global objects available to event</h4>

<code>method_request_headers</code>: The response headers for the request<br>
<code>method_request_parameters</code>: parameters for the request<br>
<code>method_request_mergefields</code>: mergefields for the request<br>
<code>method_response</code> object that contains all of the Response data.<br>
<code>cycle_variables</code>: Allows access to Cycle variables.  Changes are not persisted.<br>
<code>cycle_step_id</code>: ID of the step that is executing the script.<br>
<code>cycle_id</code>: The ID of the cycle the script is running in<br>
<code>cyclr_account_id</code>: The internal ID of the account the script is running in<br>
<code>external_account_id</code>: The external ID of the account the script is running in<br>
<code>action_data</code>: An object used to persist data between some event handler functions, allowing data to be passed between them.  Accessible in before_action, after_action, after_action_paging, action_condition and after_error.<br>
<code>return</code>: true
<hr>
</details>

<details>
<summary><b>+ after_error</b></summary>

<h4>Description</h4>

Function is called when Cyclr received an error from an external API.

<hr>

<h4>Global objects available to event</h4>

<code>method_error</code> Details of the error, see: **Handle Errors from Third Party APIs** further down for more information on handling errors<br>
<code>cycle_variables</code>: Allows access to Cycle variables.  Changes are not persisted.<br>
<code>cycle_step_id</code>: ID of the step that is executing the script.<br>
<code>cycle_id</code>: The ID of the cycle the script is running in<br>
<code>cyclr_account_id</code>: The internal ID of the account the script is running in<br>
<code>external_account_id</code>: The external ID of the account the script is running in<br>
<code>action_data</code>: An object used to persist data between some event handler functions, allowing data to be passed between them.  Accessible in before_action, after_action, after_action_paging, action_condition and after_error.<br>
<code>return</code>: true
<hr>
</details>


<details>
<summary><b>+ action_condition</b></summary>

<h4>Description</h4>

Function is used to essentially combine a Method with a Decision Step, allowing a test to be performed that directs a Transaction down either the True or False exit points.  If this function is included in a method, Cyclr will add True and False exit points.

<hr>

<h4>Global objects available to event</h4>

<code>method_response</code> object that was received from the third party API.<br>
<code>cycle_variables</code>: Allows access to Cycle variables.  Changes are not persisted.<br>
<code>cycle_step_id</code>: ID of the step that is executing the script.<br>
<code>cycle_id</code>: The ID of the cycle the script is running in<br>
<code>cyclr_account_id</code>: The internal ID of the account the script is running in<br>
<code>external_account_id</code>: The external ID of the account the script is running in<br>
<code>action_data</code>: An object used to persist data between some event handler functions, allowing data to be passed between them.  Accessible in before_action, after_action, after_action_paging, action_condition and after_error.<br>
<code>return</code>: true for the Transaction to exit on the "True Route", false to exit on the "False Route"
<hr>
</details>


<details>
<summary><b>+ before_oauth2_authorise</b></summary>

<h4>Description</h4>

Function is called before Cyclr makes an OAuth 2 authorise request.

<hr>

<h4>Global objects available to event</h4>

<code>method_endpoint</code>: URL for the OAuth authorise endpoint<br>
<code>cycle_variables</code>: Allows access to Cycle variables.  Changes are not persisted.<br>
<code>return</code>: true
<hr>
</details>

<details>
<summary><b>+ before_oauth2_token</b></summary>

<h4>Description</h4>

Called before Cyclr makes an OAuth 2 access token request.

<h4>Global objects available to event</h4>

<code>method_request_headers</code>: HTTP headers for the request<br>
<code>method_request</code>: Object that is going to be sent to the OAuth 2 access token endpoint<br>
<code>cycle_variables</code>: Allows access to Cycle variables.  Changes are not persisted.<br>
<code>return</code>: true
<hr>
</details>

<details>
<summary><b>+ after_oauth2_token</b></summary>

<h4>Description</h4>

Called after Cyclr makes an OAuth 2 access token request.

<hr>

<h4>Global objects available to event</h4>

<code>method_response</code>: response object that was received from the OAuth 2 access token request<br>
<code>cycle_variables</code>: Allows access to Cycle variables.  Changes are not persisted.<br>
<code>return</code>: true
<hr>
</details>

<details>
<summary><b>+ before_oauth2_refresh</b></summary>

<h4>Description</h4>

Called before Cyclr makes an OAuth 2 refresh token request.

<hr>

<h4>Global objects available to event</h4>

<code>method_request_headers</code>: HTTP headers for the request<br>
<code>method_request</code>: request object that is going to be sent to the OAuth 2 refresh token request<br>
<code>cycle_variables</code>: Allows access to Cycle variables.  Changes are not persisted.<br>
<code>return</code>: true
<hr>
</details>

<details>
<summary><b>+ after_oauth2_refresh</b></summary>

<h4>Description</h4>

Called after Cyclr makes an OAuth 2 refresh token request.

<hr>

<h4>Global objects available to event</h4>

<code>method_response</code>: response object that was received from the OAuth 2 refresh token request.<br>
<code>cycle_variables</code>: Allows access to Cycle variables.  Changes are not persisted.<br>
<code>return</code>: true
<hr>
</details>

> Note: The global object `method_response_fields` is an array containing the Response Fields of the method from which it is accessed.

## Functions

### General Functions 

(click to expand)

<details>
<summary><b>+ http_request</b></summary>

<h4>Description</h4>

Function to make external HTTP requests.

When calling the `http_request` function, you provide a JSON object with the following properties:

*   method: HTTP method, e.g. GET, POST, DELETE, PUT
*   url: URL for the HTTP request
*   parameters: Querystring parameters
*   headers: HTTP headers
*   data: HTTP request data.  If sending JSON, you should use JSON.stringify() to serialize it.

<hr>

#### Example Request

```javascript
function after_action() {
	var response = http_request(
		{
			'method': 'POST',
			'url': 'https://someapi.com/createsomething',
			'headers':
			{
				'Authorization': 'Bearer ' + method_auth_value,
				'Content-Type': 'application/json',
				'Accept': 'application/json'
			},
			'data': JSON.stringify( { "MyData": "some value" } )
		}
	);

	return true;
}
```

#### Response

The Response from an `http_request` call is returned as a JSON object with these properties:

*  status_code: the HTTP Status code returned
*  headers: any HTTP headers
*  content: the Response body
*  request: details of the Request that was made

<hr>

</details>

<details>
<summary><b>+ btoa</b> and <b>atob</b> (Base64 encode/decode)</summary>

<h4>Description</h4>

#### btoa

Function to encode a string using Base64.

#### atob

Function to decode a Base64 encoded string.

<hr>

#### Example


```javascript
var encoded = btoa('apple pie'); // YXBwbGUgcGll
var decoded = atob('YXBwbGUgcGll'); // apple pie

```

<hr>

</details>


<details>
<summary><b>+ cyclr_sign</b></summary>

<h4>Description</h4>

Function to sign a string with a key, using the specified algorithm.

<hr>

#### Example

```javascript
var algorithm = 'HMAC-SHA1';
var signingKey = 'This is the signing key.';
var valueToSign = 'This is the string to sign.';

var signature = cyclr_sign(algorithm, signingKey, valueToSign);
```

Supported algorithms are: `HMAC-SHA1`, `RSA-SHA1`, `RSA-SHA224`, `RSA-SHA256`, `RSA-SHA384`, `RSA-SHA512`.

<hr>

</details>

<details>
<summary><b>+ cyclr_csv_parse</b></summary>

<h4>Description</h4>

Function to parse a CSV string into JSON.

<hr>

```javascript
var csv = '1,2,3\na,b,c';
var delimiter = ',';
var hasHeader = false;

var csvRecords =  cyclr_csv_parse(csv, delimiter, hasHeader);
/* Result: 
[
    {"Field1":"1","Field2":"2","Field3":"3"},
    {"Field1":"a","Field2":"b","Field3":"c"}
]
*/
```

<hr>

</details>

### Storage Functions

Cyclr provides several storage functions available for use in Script that can be used when developing a Connector, or on a Step in a Template or Cycle.

Data they work against is locked to the Connector they're called on.  i.e. if you write data using `cyclr_storage_set()` on a Step from one Connector, you cannot access that same data using `cyclr_storage_get()` on a Step from a different Connector.

The functions come in 2 flavours:

`cyclr_storage_...()` and `cycle_storage_...()`

The `cyclr_storage_...()` functions access the same data on any Steps in any Cycles for a particular Connector.

The `cycle_storage_...()` functions work in the same way, but their data is further restricted to the context of a particular Cycle.  If you write data in one Cycle, you cannot access it in another;

The storage functions available in their `cyclr_` versions are shown below.

Change `cyclr_` to `cycle_` to use their Cycle-restricted versions.

* cyclr_storage_list_values()
* cyclr_storage_delete_all()
* cyclr_storage_delete(key)
* cyclr_storage_get(key)
* cyclr_storage_set(key, value)
* cyclr_storage_append(key, value)
* cyclr_storage_list_keys()


### Exceptions

Exceptions can be thrown from script to force reauthentication.

There are two types (click to expand):

<details>
<summary><b>+ AuthRefreshException</b></summary>

<h4>Description</h4>

Exception to force the OAuth 2 authentication token to be refreshed.

This is useful when the OAuth 2 endpoint doesn't return a definite token expiry time.

Upon getting this exception, Cyclr will call the OAuth 2 *Access Token URL* to get a new access token.

For example, an API returns 200 with an error code in the response when the token becomes invalid:

```javascript
function after_action() {
    if (typeof method_response.error !== 'undefined' &&
        method_response.error === 'invalid_grant') {
        throw new AuthRefreshException();
    }
    return true;
}
```

If an API returns a non-2xx HTTP status code when the auth token becomes invalid, you should throw *AuthRefreshException* in *after_error*:
```javascript
function after_error() {
    if (method_error.statusCode.toString() == 403) {
        throw new AuthRefreshException();
    }
    return true;
}
```

<hr>

</details>

<details>
<summary><b>+ AuthSessionException</b></summary>

<h4>Description</h4>

Exception to force the authentication session to be refreshed.

Upon getting this exception, Cyclr will call the *Post Install Property Value Lookup Method* to start a new session.

For example, an API returns 200 with an error code in the response when the session expires:

```javascript
function after_action() {
    if (typeof method_response.error_code !== 'undefined' &&
        method_response.error_code === 'You are not logged on.') {
        throw new AuthSessionException();
    }
    return true;
}
```

If an API returns a non-2xx HTTP status code when the auth session expires, you should throw *AuthSessionException* in *after_error*:
```javascript
function after_error() {
    if (method_error.statusCode.toString() == 403) {
        throw new AuthSessionException();
    }
    return true;
}
```

<hr>

</details>

### Libraries

The following libraries are available within Cyclr's script engine:

> NB. It is not necessary to load these with a `require` call, they are ready to use in script.

#### Moment.js

Library Name: moment

Description: Parse, validate, manipulate, and display dates and times in JavaScript.
Cyclr also supports the Moment Timezone extension, which enables formatting and converting of dates in any timezone.

External Documentation: <https://momentjs.com/>, <https://momentjs.com/timezone/>


#### CryptoJS

Library Name: crypto-js

Description: JavaScript library of crypto standards.

Warning: The output of encrypted data is always in a hex string. Formatting options `CryptoJS.enc` are not supported when calling `toString`.

External Documentation: <https://github.com/brix/crypto-js>

### Connector scripting examples

(Click to expand)

<details>
    <summary><b>+ Making External Requests</b></summary>

<h4>Description</h4>

You can write a script to call external API endpoints. This is especially useful if the API returns a URL which contains the real response object.

For example, a webhook returns the following object to Cyclr:

```json
{
    "event": "object.updated",
    "api_url": "http://httpbin.org/get"
}
```

Use `http_request` to call `api_url` and replace the webhook response with the updated object:

```javascript
function after_webhook() {
    var request = {
        'method': 'GET',
        'url': method_response.api_url,
        'headers': {
            'Accept': 'application/json'
        }
    };

    var content = http_request(request).content;
    method_response = content;
    return true;
}
```
    

After calling `api_url`, Cyclr will then replace `method_response` with the content of the HTTP call.

Return `false` in the `after_webhook` function will stop Cyclr from running the webhook. You can use this trick to filter webhook events.

<hr>

</details>

<details>
    <summary><b>+ Transforming Key Value Pairs</b></summary>

<h4>Description</h4>

Making use of key value pair responses requires the use of scripting, consider an API that returns the below representation of a contact.

```json
{
    properties: [{
        "key": "email",
        "value": "example@example.com"
    }]
}
```

To access the email field we would add a field in the method response with a connector location of **properties.email**. However this would not work as the cyclr is looking in the response for a properties object with a property named email to get the value from. To solve the issue we would add the below function into the method scripts, this function will transform the properties array into an object with properties for each key value pair.

```javascript
function after_action() {
    var original = method_response.properties;
    method_response.properties = {};

    for (var i = 0; i < original.length; i++) {
        var item = original[i];
        if (item['key'] == void(0))
            continue;

        var val = item['value'];
        if (val == void(0))
            continue;

        method_response.properties[item['key']] = val;
    }

    return true;
}
```
    

Now when cyclr runs the method if will get the following result back and the **properties.email** field will work as expected.

```json
{
    properties: {
        "email": "example@example.com"
    }
}
```    

For a corresponding request method, e.g. adding a contact, we would need the below function in the method scripts to perform the data transformation in reverse.

```javascript
function before_action() {
    var original = method_request.properties;
    method_request.properties = [];

    for (var p in original) {
        method_request.properties.push({
            'key': p,
            'value': original[p]
        });
    }
    return true;
}
```

<hr>

</details>

<details>
    <summary><b>+ Modifying Parameters</b></summary>

<h4>Description</h4>

Besides the HTTP request body, you can also use scripting to modify HTTP headers (`method_request_headers`) and query string parameters (`method_request_parameters`).

```javascript
function before_action() {
    var xmlData = '<Records><Record>';

    for (var p in method_request) {
        xmlData += '<Field val=""' + p + '"">' + method_request[p] + '</Field>';
    }

    xmlData += '</Record></Records>';
    method_request_parameters.xmlData = xmlData;
    return true;
}
```    

In this example, we transformed the method request body to a XML string and saved the string as a new parameter called `xmlData`.

<hr>

</details>

<details>
    <summary><b>+ Handling Errors from Third Party APIs</b></summary>

<h4>Description</h4>

The scripting engine can be used to catch and handle errors returned from third party APIs.

Cyclr exposes a received error response in the `after_error` function through the `method_error` object, which has these properties:
<br>
<code>statusCode</code> – the HTTP status code returned by the third party API<br>
<code>reasonPhrase</code> – the reason phrase returned by the third party API<br>
<code>content</code> – the body content of the response from the third party API<br>
<code>isError</code> – indicates that the error is an error. default: true, set to false if using isWarning or isSuccess<br>
<code>isWarning</code> – set to true for Cyclr to log the error as a warning<br>
<code>isSuccess</code> – set to true to change the error to success, update content to contain the success step data

Example: change an error to a warning

```javascript
function after_error() {
    if (method_error.statusCode.toString() == 400 && method_error.reasonPhrase == 'Email Address not valid') {
        method_error.isError = false;
        method_error.isWarning = true;
    }
    return true;
}
```

Example: change an error to a success

```javascript
function after_error() {
    if (method_error.statusCode.toString() == 400 && method_error.reasonPhrase == 'Email Address not valid') {
        method_error.isError = false;
        method_error.isSuccess = true;
        method_error.content = '{}';
    }
    return true;
}
```    

<hr>

</details>

### Script Testing
If you want to test your Javascript functions outside of a cycle, you can use the [Script Tester](https://docs.cyclr.com/script-tester).

### Limitations

*   Execution time: 60 seconds. Script running will time out after 60 seconds.
*   External HTTP requests: for security reasons, we will use the same authentication method as the connector and the same authentication value when the connector was installed by the user. You cannot use the script to access or modify the authentication value.
*   The **cycle_variables** object is only available through a Step's Advanced Settings area, and not through Inline Script.  Also, any changes made to it and its properties are not persisted.
