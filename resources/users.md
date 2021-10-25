---
description: >-
  Users are key component of building basically any system now. Here is
  described everything you need to know about users resource.
---

# Users

{% swagger baseUrl="https://api.hyperia.space" path="/users/v1/:id" method="get" summary="Get user" %}
{% swagger-description %}
Request user information by the 

`id`
{% endswagger-description %}

{% swagger-parameter name="id" type="string" in="path" required="true" %}
ID of the user to retrieve
{% endswagger-parameter %}

{% swagger-response status="200" description="Request is successful" %}
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

{% hint style="info" %}
The update endpoint requires `MANAGE_USERS` permission if the authorized user isn't the account owner.
{% endhint %}

{% hint style="warning" %}
The `password` field is accessible only if the authorized user is the account owner. Otherwise fires `CANNOT_CHANGE_USER_PASSWORD` error.
{% endhint %}

{% hint style="warning" %}
The `perms` field requires authorized user to have `MANAGE_PERMISSIONS permission. If `authorized user lacks it, fires `CANNOT_CHANGE_USER_PERMISSIONS` error.
{% endhint %}

{% swagger baseUrl="https://api.hyperia.space" path="/users/v1/:id" method="put" summary="Update user" %}
{% swagger-description %}
Updates the user info and returns the old one
{% endswagger-description %}

{% swagger-parameter name="id" type="string" in="path" required="true" %}
ID of the user to update
{% endswagger-parameter %}

{% swagger-parameter name="Authorization" type="string" in="header" required="false" %}
Authentication token to acknowledge who is making updates to the user
{% endswagger-parameter %}

{% swagger-parameter name="avoidEmpty" type="boolean" in="query" required="false" %}
Avoid empty fields. If is false or not set the endpoint will make sure every single field is filled
{% endswagger-parameter %}

{% swagger-parameter name="includeChanged" type="boolean" in="query" required="false" %}
If is set and true, the endpoint includes only changed fields in the response
{% endswagger-parameter %}

{% swagger-parameter name="nick" type="string" in="body" required="true" %}
New user nickname, must be unique
{% endswagger-parameter %}

{% swagger-parameter name="email" type="string" in="body" required="true" %}
New user email
{% endswagger-parameter %}

{% swagger-parameter name="password" type="string" in="body" required="true" %}
Updated user password
{% endswagger-parameter %}

{% swagger-parameter name="avatarUrl" type="string" in="body" required="false" %}
Updated avatar URL
{% endswagger-parameter %}

{% swagger-parameter name="perms" type="string" in="body" required="false" %}
Updated user permissions
{% endswagger-parameter %}

{% swagger-response status="200" description="Update was successful" %}
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

{% swagger baseUrl="https://api.hyperia.space" path="/users/v1/:id" method="delete" summary="Delete user" %}
{% swagger-description %}
Deletes the user specified by 

`id`

 and returns the user info
{% endswagger-description %}

{% swagger-parameter name="id" type="string" in="path" required="true" %}
ID of the user to delete
{% endswagger-parameter %}

{% swagger-parameter name="Authorization" type="string" in="header" required="true" %}
Authentication token to acknowledge who is deleting the user
{% endswagger-parameter %}

{% swagger-response status="200" description="Deletion is successful" %}
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

## Permissions

| Name                 | Value    | Description                                                                     |
| -------------------- | -------- | ------------------------------------------------------------------------------- |
| `MANAGE_RESOURCES`   | `1 << 0` | <p>This permission allows user to</p><p>manage non-owned communities</p>        |
| `MANAGE_USERS`       | `1 << 1` | <p>This permission allows user to</p><p>manage user's info. Except password</p> |
| `MANAGE_PERMISSIONS` | `1 << 2` | <p>This permission allows user to</p><p>change other user's permissions</p>     |

