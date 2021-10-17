---
description: >-
  This page describes our authentication flow: how it's done, where to get the
  tokens and how is this all working, please help me!!!
---

# Authentication

## Endpoints

{% swagger baseUrl="https://api.hyperia.space" path="/auth/v1/login" method="post" summary="Authenticate" %}
{% swagger-description %}
Checks credentials and returns the token pair
{% endswagger-description %}

{% swagger-parameter name="nick" type="string" in="body" %}
User nickname
{% endswagger-parameter %}

{% swagger-parameter name="password" type="string" in="body" %}
User password
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```javascript
{
    "accessToken": "YOUR-ACCESS-TOKEN",
    "refreshToken": "YOUR-REFRESH-TOKEN"
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://api.hyperia.space" path="/auth/v1/refresh" method="put" summary="Refresh token pair" %}
{% swagger-description %}
Refreshes the token pair and returns a new one
{% endswagger-description %}

{% swagger-parameter name="accessToken" type="string" in="body" %}
Access token to refresh
{% endswagger-parameter %}

{% swagger-parameter name="refreshToken" type="string" in="body" %}
Refresh token to refresh the token pair
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```javascript
{
    "accessToken": "YOUR-NEW-ACCESS-TOKEN",
    "refreshToken": "YOUR-NEW-REFRESH-TOKEN"
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://api.hyperia.space" path="/auth/v1/revoke" method="post" summary="Revoke token pair" %}
{% swagger-description %}
Revokes the token pair
{% endswagger-description %}

{% swagger-parameter name="accessToken" type="string" in="body" %}
Access token to revoke
{% endswagger-parameter %}

{% swagger-parameter name="refreshToken" type="string" in="body" %}
Refresh token to revoke
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```javascript
{}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://api.hyperia.space" path="/auth/v1/validate" method="get" summary="Validate" %}
{% swagger-description %}
Validates the token and returns the results
{% endswagger-description %}

{% swagger-parameter name="accessToken" type="string" in="query" %}
Access token to validate
{% endswagger-parameter %}

{% swagger-parameter name="refreshToken" type="string" in="query" %}
If specified - validates the token pair
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```javascript
{ "value": true }
```
{% endswagger-response %}
{% endswagger %}
