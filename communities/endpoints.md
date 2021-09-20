---
description: Community-related endpoints.
---

# Endpoints

{% api-method method="post" host="https://api.hyperia.space" path="/communities/v1/new" %}
{% api-method-summary %}
Create a community
{% endapi-method-summary %}

{% api-method-description %}
Creates a new community
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=false %}
Authentication token to acknowledge who is creating the community
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="name" type="string" required=true %}
Community name.
{% endapi-method-parameter %}

{% api-method-parameter name="desc" type="string" required=true %}
Community description.
{% endapi-method-parameter %}

{% api-method-parameter name="kind" type="integer" required=true %}
Community kind
{% endapi-method-parameter %}

{% api-method-parameter name="link" type="string" required=true %}
Link to the community.
{% endapi-method-parameter %}

{% api-method-parameter name="avatar\_url" type="string" required=false %}
Community's avatar. If left blank, fetches avatar automatically based on `kind` \(platform\). Or if `kind`set to custom website, uses default avatar.
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Id of newly created community
{% endapi-method-response-example-description %}

```javascript
{
    "id": "795aeb50-1b48-4aae-8700-8d9101845741"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://api.hyperia.space" path="/communities/v1/:id" %}
{% api-method-summary %}
Get a community
{% endapi-method-summary %}

{% api-method-description %}
Retrieves the community by given id.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
Community id
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=false %}
Authentication token to identify who is making the request
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Community exists and retrieved.
{% endapi-method-response-example-description %}

```javascript
{
    "name": "Server-Discord.com",
    "description": "Server Discord is a powerful Discord server monitoring",
    "link": "https://sdc.su",
    "owner": "85cacde9-7f62-48c3-af06-1d2d14eade6b",
    "kind": 5
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="put" host="https://api.hyperia.space" path="/communities/v1/:id" %}
{% api-method-summary %}
Update a community
{% endapi-method-summary %}

{% api-method-description %}
Updates community and returns changes.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
Community id
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
Authentication token to identify the user updating the community
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-query-parameters %}
{% api-method-parameter name="avoid\_empty" type="boolean" required=false %}
Avoids empty fields in the request. Otherwise the endpoint will throw a error if field has incorrect value or empty.
{% endapi-method-parameter %}

{% api-method-parameter name="include\_changed" type="boolean" required=false %}
Include only changed fields in the response
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="name" type="string" required=false %}
New community name
{% endapi-method-parameter %}

{% api-method-parameter name="desc" type="string" required=false %}
New community description
{% endapi-method-parameter %}

{% api-method-parameter name="kind" type="integer" required=false %}
New community kind
{% endapi-method-parameter %}

{% api-method-parameter name="link" type="string" required=false %}
New community link
{% endapi-method-parameter %}

{% api-method-parameter name="avatar\_url" type="string" required=false %}
New community avatar
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Community info before the update \(with \`old\_\` prefix in a field\) and updated info. If \`include\_changed\` is \`true\` - includes only changed field pairs.
{% endapi-method-response-example-description %}

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
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="delete" host="https://api.hyperia.space" path="/communities/v1/:id" %}
{% api-method-summary %}
Delete community
{% endapi-method-summary %}

{% api-method-description %}
Deletes the community and returns it's info
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
Community id to delete
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
Authentication token to acknowledge who deletes the community
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Community info before the deletion
{% endapi-method-response-example-description %}

```javascript
{
    "name": "Community name",
    "description": "Community description",
    "link": "https://link.to/community",
    "owner": "owner-id",
    "kind": 1
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="put" host="https://api.hyperia.space" path="/communities/v1/:id/transfer" %}
{% api-method-summary %}
Transfer ownership
{% endapi-method-summary %}

{% api-method-description %}
Transfers ownership of the community. Returns old and new owner IDs.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
Community id to transfer ownership of
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
Authentication token to authorize the owner of the community
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="new\_owner" type="string" required=true %}
Id of new community owner
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
    "old_owner": "old-owner-id",
    "owner": "new-owner-id"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

