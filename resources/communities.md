---
description: >-
  Community is an atomic entity in our API. It represents a Discord server put
  on Hyperia, for advertisement and gathering of even more people!
---

# Communities

{% swagger baseUrl="https://api.hyperia.space" path="/communities/v1/new" method="post" summary="Create a community" %}
{% swagger-description %}
Creates a new community
{% endswagger-description %}

{% swagger-parameter name="Authorization" type="string" in="header" required="true" %}
Authentication token to acknowledge who is creating the community
{% endswagger-parameter %}

{% swagger-parameter name="name" type="string" in="body" required="false" %}
Community name.
{% endswagger-parameter %}

{% swagger-parameter name="desc" type="string" in="body" required="false" %}
Community description.
{% endswagger-parameter %}

{% swagger-parameter name="kind" type="integer" in="body" required="false" %}
Community kind
{% endswagger-parameter %}

{% swagger-parameter name="link" type="string" in="body" required="false" %}
Link to the community.
{% endswagger-parameter %}

{% swagger-parameter name="avatar_url" type="string" in="body" required="false" %}
Community's avatar. If left blank, fetches avatar automatically based on

`kind`

(platform). Or if

`kind`

set to custom website, uses default avatar.
{% endswagger-parameter %}

{% swagger-response status="200" description="Creation was successful" %}
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

{% swagger-parameter name="id" type="string" in="path" required="false" %}
Community id
{% endswagger-parameter %}

{% swagger-parameter name="Authorization" type="string" in="header" required="false" %}
Authentication token to identify who is making the request
{% endswagger-parameter %}

{% swagger-response status="200" description="Community exists and request was successful " %}
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

{% swagger-parameter name="id" type="string" in="path" required="true" %}
Community id
{% endswagger-parameter %}

{% swagger-parameter name="Authorization" type="string" in="header" required="true" %}
Authentication token to identify the user updating the community
{% endswagger-parameter %}

{% swagger-parameter name="avoid_empty" type="boolean" in="query" required="false" %}
Avoids empty fields in the request. Otherwise the endpoint will throw a error if field has incorrect value or empty.
{% endswagger-parameter %}

{% swagger-parameter name="include_changed" type="boolean" in="query" required="false" %}
Include only changed fields in the response
{% endswagger-parameter %}

{% swagger-parameter name="name" type="string" in="body" required="false" %}
New community name
{% endswagger-parameter %}

{% swagger-parameter name="desc" type="string" in="body" required="false" %}
New community description
{% endswagger-parameter %}

{% swagger-parameter name="kind" type="integer" in="body" required="false" %}
New community kind
{% endswagger-parameter %}

{% swagger-parameter name="link" type="string" in="body" required="false" %}
New community link
{% endswagger-parameter %}

{% swagger-parameter name="avatar_url" type="string" in="body" required="false" %}
New community avatar
{% endswagger-parameter %}

{% swagger-response status="200" description="Update was successful" %}
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

{% swagger-parameter name="id" type="string" in="path" required="true" %}
Community id to delete
{% endswagger-parameter %}

{% swagger-parameter name="Authorization" type="string" in="header" required="true" %}
Authentication token to acknowledge who deletes the community
{% endswagger-parameter %}

{% swagger-response status="200" description="Deletion was successful" %}
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

{% swagger-parameter name="id" type="string" in="path" required="true" %}
Community id to transfer ownership of
{% endswagger-parameter %}

{% swagger-parameter name="Authorization" type="string" in="header" required="true" %}
Authentication token to authorize the owner of the community
{% endswagger-parameter %}

{% swagger-parameter name="new_owner" type="string" in="body" required="true" %}
Id of new community owner
{% endswagger-parameter %}

{% swagger-response status="200" description="Transfer was successful" %}
```javascript
{
    "old_owner": "old-owner-id",
    "owner": "new-owner-id"
}
```
{% endswagger-response %}
{% endswagger %}

## Community kinds

The community that you built might be based on a wide variety of platforms. Whenever this will be a gaming Discord server, an amazing GitHub project or just a website. Hyperia supports most popular of them. Our main goal was to an advertisement platform not only for a single platform, but give people ability to advertise their websites, projects or communities wherever they are built.

Here is currently supported community platforms:

| Platform        | Representation in API |
| --------------- | --------------------- |
| Discord         | `0x1`                 |
| VK (VKontake)   | `0x2`                 |
| FB (Facebook)   | `0x4`                 |
| Custom websites | `0x5`                 |

In the future the list will increase. Feel free to suggest a platform in our feedback page, or in our [Discord server](https://discord.gg/Hz5GMFS).
