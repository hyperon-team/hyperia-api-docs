---
description: Community-related endpoints.
---

# Endpoints

{% swagger baseUrl="https://api.hyperia.space" path="/communities/v1/new" method="post" summary="Create a community" %}
{% swagger-description %}
Creates a new community
{% endswagger-description %}

{% swagger-parameter name="Authorization" type="string" in="header" %}
Authentication token to acknowledge who is creating the community
{% endswagger-parameter %}

{% swagger-parameter name="name" type="string" in="body" %}
Community name.
{% endswagger-parameter %}

{% swagger-parameter name="desc" type="string" in="body" %}
Community description.
{% endswagger-parameter %}

{% swagger-parameter name="kind" type="integer" in="body" %}
Community kind
{% endswagger-parameter %}

{% swagger-parameter name="link" type="string" in="body" %}
Link to the community.
{% endswagger-parameter %}

{% swagger-parameter name="avatar:url" type="string" in="body" %}
Community's avatar. If left blank, fetches avatar automatically based on 

`kind`

 (platform). Or if 

`kind`

set to custom website, uses default avatar.
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```javascript
{
    "id": "795aeb50-1b48-4aae-8700-8d9101845741"
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://api.hyperia.space" path="/communities/v1/:id" method="get" summary="Get a community" %}
{% swagger-description %}
Retrieves the community by given id.
{% endswagger-description %}

{% swagger-parameter name="id" type="string" in="path" %}
Community id
{% endswagger-parameter %}

{% swagger-parameter name="Authorization" type="string" in="header" %}
Authentication token to identify who is making the request
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```javascript
{
    "name": "Server-Discord.com",
    "description": "Server Discord is a powerful Discord server monitoring",
    "link": "https://sdc.su",
    "owner": "85cacde9-7f62-48c3-af06-1d2d14eade6b",
    "kind": 5
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://api.hyperia.space" path="/communities/v1/:id" method="put" summary="Update a community" %}
{% swagger-description %}
Updates community and returns changes.
{% endswagger-description %}

{% swagger-parameter name="id" type="string" in="path" %}
Community id
{% endswagger-parameter %}

{% swagger-parameter name="Authorization" type="string" in="header" %}
Authentication token to identify the user updating the community
{% endswagger-parameter %}

{% swagger-parameter name="avoid:empty" type="boolean" in="query" %}
Avoids empty fields in the request. Otherwise the endpoint will throw a error if field has incorrect value or empty.
{% endswagger-parameter %}

{% swagger-parameter name="include:changed" type="boolean" in="query" %}
Include only changed fields in the response
{% endswagger-parameter %}

{% swagger-parameter name="name" type="string" in="body" %}
New community name
{% endswagger-parameter %}

{% swagger-parameter name="desc" type="string" in="body" %}
New community description
{% endswagger-parameter %}

{% swagger-parameter name="kind" type="integer" in="body" %}
New community kind
{% endswagger-parameter %}

{% swagger-parameter name="link" type="string" in="body" %}
New community link
{% endswagger-parameter %}

{% swagger-parameter name="avatar:url" type="string" in="body" %}
New community avatar
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```javascript
{
    "old_name": "Old community name",
    "name": "New community name",
    "old_desc": "Old description",
    "desc": "New description",
    "old_link": "https://link.to/old_community",
    "link": "https://link.to/community",
    "old_kind": 1,
    "new_kind": 2
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://api.hyperia.space" path="/communities/v1/:id" method="delete" summary="Delete community" %}
{% swagger-description %}
Deletes the community and returns it's info
{% endswagger-description %}

{% swagger-parameter name="id" type="string" in="path" %}
Community id to delete
{% endswagger-parameter %}

{% swagger-parameter name="Authorization" type="string" in="header" %}
Authentication token to acknowledge who deletes the community
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```javascript
{
    "name": "Community name",
    "description": "Community description",
    "link": "https://link.to/community",
    "owner": "owner-id",
    "kind": 1
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://api.hyperia.space" path="/communities/v1/:id/transfer" method="put" summary="Transfer ownership" %}
{% swagger-description %}
Transfers ownership of the community. Returns old and new owner IDs.
{% endswagger-description %}

{% swagger-parameter name="id" type="string" in="path" %}
Community id to transfer ownership of
{% endswagger-parameter %}

{% swagger-parameter name="Authorization" type="string" in="header" %}
Authentication token to authorize the owner of the community
{% endswagger-parameter %}

{% swagger-parameter name="new:owner" type="string" in="body" %}
Id of new community owner
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```javascript
{
    "old_owner": "old-owner-id",
    "owner": "new-owner-id"
}
```
{% endswagger-response %}
{% endswagger %}
