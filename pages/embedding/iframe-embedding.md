---
title: Embedding Cyclr in an iFrame
sidebar: cyclr_sidebar
permalink: iframe-embedding
tags: [embedding]
---

To embed Cyclr in an iFrame, you will need to take the following steps:

1. Obtain an access token
2. Use the access token to get a User-Specific Sign-in Token
3. Generate the source URL for your iFrame.

### 1. Obtaining an access token

#### Get Client ID and Secret

You can generate a Client ID and Secret from the Cyclr Partner Console, Settings > OAuth Client Credentials

![Cyclr Console OAuth Client Credentials](./images/cyclr-api-client-credentials.png)

Once you have a Client ID and Secret you need to call the Cyclr API OAuth token endpoint to generate an access token.  This endpoint will be different depending on where your Cyclr Console is hosted:

Cyclr Console Location | API Domain
--- | ---
my.cyclr.com | https://api.cyclr.com/oauth/token
my.cyclr.uk | https://api.cyclr.uk/oauth/token
eu.cyclr.com | https://api.eu.cyclr.com/oauth/token

#### Required Request Body Parameters

| Parameter | Description | Example |
| --- | --- | --- |
| grant_type | Identifies the OAuth flow being used. Must be client_credentials | client_credentials |
| client_id | Identifies the Cyclr Partner the token is for | abcdefg |
| client_secret | The matching secret for the client ID | abcdefghij123 |

#### Example Request

```http
POST https://{API Domain}/oauth/token
Content-Type: application/x-www-form-urlencoded

grant_type=client_credentials&client_id=abcdefg&client_secret=abcdefghij123
```
> NB. ``grant_type``, ``client_id`` and ``client_secret`` go in the body of the call - they are not added to the endpoint.

#### Example Response

```json
{
    "token_type": "bearer",
    "access_token": "************",
    "expires_in": 1209599,
    "clientId": "************"
}
```

### 2. Generating a User-Specific Sign-in Token

For this stage, you'll need the access token from the previous step, and the Cyclr Account's API ID.

If you need to find the value, in your Console, go to Accounts then find the Account you want to work with, edit it and you'll see API ID near the top:

![](./images/API_ID.png)

Make a call to 

```http
POST https://api.eu.cyclr.com/v1.0/accounts/{API ID}/signintoken
Content-Type: application/json

{
	"Username" : "Replace this text with your desired username"
}
```

This will return a response like this:

````json
{
  "Token": "JWxm_cYOq0m6PYWcVPWpuSBP-ppqRwhBkfXTYFE3Xk0",
  "ExpiresAtUtc": "2021-05-17T15:55:41.9993413Z"
}
````

You'll notice this token will expire in 5 minutes.  You can use this to complete the src of your iframe, which will look something like this:

```html
<iframe src="https://{YOURSERVICEDOMAIN}/account/signinwithtoken?token=TOKENFROMPREVIOUSSTAGE"> 
```

### Final Steps

You will need to check that iFrame Embedding is turned ON in your Console's general settings, and that you have added your domain to the Host Whitelist.

The host will need to use SSL, for security reasons.
