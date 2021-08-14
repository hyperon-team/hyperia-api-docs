---
description: >-
  This page describes our authentication flow: how it's done, where to get the
  tokens and how is this all working, please help me!!!
---

# Authentication

## Endpoints

{% api-method method="post" host="https://api.hyperia.space" path="/v1/login" %}
{% api-method-summary %}
Authenticate
{% endapi-method-summary %}

{% api-method-description %}
Checks credentials and returns the token pair
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="nick" type="string" required=true %}
User nickname
{% endapi-method-parameter %}

{% api-method-parameter name="password" type="string" required=true %}
User password
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "accessToken": "YOUR-ACCESS-TOKEN",
    "refreshToken": "YOUR-REFRESH-TOKEN"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="put" host="https://api.hyperia.space" path="/v1/auth/refresh" %}
{% api-method-summary %}
Refresh token pair
{% endapi-method-summary %}

{% api-method-description %}
Refreshes the token pair and returns a new one
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="" type="string" required=false %}

{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="https://api.hyperia.space" path="/auth/v1/revoke" %}
{% api-method-summary %}
Revoke token pair
{% endapi-method-summary %}

{% api-method-description %}
Revokes the token pair
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="accessToken" type="string" required=true %}
Access token to revoke
{% endapi-method-parameter %}

{% api-method-parameter name="refreshToken" type="string" required=true %}
Refresh token to revoke
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "accessToken": "YOUR-NEW-ACCESS-TOKEN",
    "refreshToken": "YOUR-NEW-REFRESH-TOKEN"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://api.hyperia.space" path="/auth/v1/validate" %}
{% api-method-summary %}
Validate
{% endapi-method-summary %}

{% api-method-description %}
Validates the token and returns the results
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="accessToken" type="string" required=true %}
Access token to validate
{% endapi-method-parameter %}

{% api-method-parameter name="refreshToken" type="string" required=false %}
If specified - validates the token pair
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

