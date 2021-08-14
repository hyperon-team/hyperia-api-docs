---
description: User-related endpoints
---

# Endpoints

{% api-method method="get" host="https://api.hyperia.space" path="/users/v1/:id" %}
{% api-method-summary %}
Get user by ID
{% endapi-method-summary %}

{% api-method-description %}
Get user info by his ID
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
ID of the user to retrieve
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "id": "user-id",
    "nick": "MegaVasily007",
    "email": "admin@mail.sdc.su",
    "perms": 0
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="delete" host="https://api.hyperia.space" path="/users/v1/:id" %}
{% api-method-summary %}
Delete user
{% endapi-method-summary %}

{% api-method-description %}
Deletes the user and returns user's info before deletion
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
ID of the user to delete
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=false %}
Authentication token to acknowledge who is deleting the user
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "id": "user-id",
    "nick": "MegaVasily007",
    "email": "admin@mail.sdc.su",
    "perms": 0
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="put" host="https://api.hyperia.space" path="/users/v1/:id" %}
{% api-method-summary %}
Update user
{% endapi-method-summary %}

{% api-method-description %}
Updates the user info and returns the old one
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
ID of the user to update
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=false %}
Authentication token to acknowledge who is making updates to the user
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-query-parameters %}
{% api-method-parameter name="avoidEmpty" type="boolean" required=false %}
Avoid empty fields. If is false or not set the endpoint will make sure every single field is filled
{% endapi-method-parameter %}

{% api-method-parameter name="includeChanged" type="boolean" required=false %}
If set to true, the endpoint includes only changed fields in the response
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="nick" type="string" required=false %}
New user nickname, must be unique
{% endapi-method-parameter %}

{% api-method-parameter name="email" type="string" required=false %}
New user email
{% endapi-method-parameter %}

{% api-method-parameter name="password" type="string" required=false %}
Updated user password.
{% endapi-method-parameter %}

{% api-method-parameter name="avatarUrl" type="string" required=false %}
Updated avatar URL
{% endapi-method-parameter %}

{% api-method-parameter name="perms" type="string" required=false %}
Updated user permissions
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    "id": "user-id",
    "nick": "MegaVasily007",
    "email": "admin@mail.sdc.su",
    "perms": 0
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% hint style="info" %}
This endpoint requires `MANAGE_USERS` permission if the authorized user isn't the account owner.
{% endhint %}

{% hint style="warning" %}
The `password` field is accessible only if the authorized user is the account owner. Otherwise fires `CANNOT_CHANGE_USER_PASSWORD` error.
{% endhint %}

{% hint style="warning" %}
The `perms` field requires authorized user to have `MANAGE_PERMISSIONS permission.`If authorized user lacks it, fires `CANNOT_CHANGE_USER_PERMISSIONS` error.
{% endhint %}

