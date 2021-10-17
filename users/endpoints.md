---
description: User-related endpoints
---

# Endpoints

{% swagger baseUrl="https://api.hyperia.space" path="/users/v1/:id" method="get" summary="Get user by ID" %}
{% swagger-description %}
Get user info by his ID
{% endswagger-description %}

{% swagger-parameter name="id" type="string" in="path" %}
ID of the user to retrieve
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```javascript
{
    "id": "user-id",
    "nick": "MegaVasily007",
    "email": "admin@mail.sdc.su",
    "perms": 0
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://api.hyperia.space" path="/users/v1/:id" method="delete" summary="Delete user" %}
{% swagger-description %}
Deletes the user and returns user's info before deletion
{% endswagger-description %}

{% swagger-parameter name="id" type="string" in="path" %}
ID of the user to delete
{% endswagger-parameter %}

{% swagger-parameter name="Authorization" type="string" in="header" %}
Authentication token to acknowledge who is deleting the user
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```javascript
{
    "id": "user-id",
    "nick": "MegaVasily007",
    "email": "admin@mail.sdc.su",
    "perms": 0
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://api.hyperia.space" path="/users/v1/:id" method="put" summary="Update user" %}
{% swagger-description %}
Updates the user info and returns the old one
{% endswagger-description %}

{% swagger-parameter name="id" type="string" in="path" %}
ID of the user to update
{% endswagger-parameter %}

{% swagger-parameter name="Authorization" type="string" in="header" %}
Authentication token to acknowledge who is making updates to the user
{% endswagger-parameter %}

{% swagger-parameter name="avoidEmpty" type="boolean" in="query" %}
Avoid empty fields. If is false or not set the endpoint will make sure every single field is filled
{% endswagger-parameter %}

{% swagger-parameter name="includeChanged" type="boolean" in="query" %}
If set to true, the endpoint includes only changed fields in the response
{% endswagger-parameter %}

{% swagger-parameter name="nick" type="string" in="body" %}
New user nickname, must be unique
{% endswagger-parameter %}

{% swagger-parameter name="email" type="string" in="body" %}
New user email
{% endswagger-parameter %}

{% swagger-parameter name="password" type="string" in="body" %}
Updated user password.
{% endswagger-parameter %}

{% swagger-parameter name="avatarUrl" type="string" in="body" %}
Updated avatar URL
{% endswagger-parameter %}

{% swagger-parameter name="perms" type="string" in="body" %}
Updated user permissions
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
    "id": "user-id",
    "nick": "MegaVasily007",
    "email": "admin@mail.sdc.su",
    "perms": 0
}
```
{% endswagger-response %}
{% endswagger %}

{% hint style="info" %}
This endpoint requires `MANAGE_USERS` permission if the authorized user isn't the account owner.
{% endhint %}

{% hint style="warning" %}
The `password` field is accessible only if the authorized user is the account owner. Otherwise fires `CANNOT_CHANGE_USER_PASSWORD` error.
{% endhint %}

{% hint style="warning" %}
The `perms` field requires authorized user to have `MANAGE_PERMISSIONS permission.`If authorized user lacks it, fires `CANNOT_CHANGE_USER_PERMISSIONS` error.
{% endhint %}
