---
description: Description and walkthrough on errors
---

# Errors

To be honest... the errors is the hardest part in working with API: you need to come up with a single standard, which unifies all needs of the API to return some kind of errors, you need to implement that. But for developer, who is using our API, we want to provide the best experience in handling errors. So, here we go

## Error response structure

Our error response \(as seen below\) contains multiple fields. The `code` field represents a unique error code for each situation that the API has encountered with processing your request: whenever this'll be some syntax error, a request of non-existing user or other variety of such errors. The `message` field contains a human-readable message, so it mustn't be handled by wrapper, bot at all, only the code. And the last but not least field: `details` contains additional information on the error. For example, in case of sending incorrect fields in the request there will be a list of fields values of which weren't specified correctly.

```javascript
{
    "code": "BAD_REQUEST",
    "message": "Never gonna give you UNAVAILABLE, never gonna let myself be down",
    "details": [
        {
            "type": "FIELD_VIOLATION",
            "field": "rules",
            "message": "You know the rules so do I"
        },
        {
            "type": "FIELD_VIOLATION",
            "field": "feeling",
            "message": "And if you ask me how I'm feeling"
        }
    ],
}
```

For more information about error codes go here:

{% page-ref page="opcodes-and-status-codes.md" %}

## Details

Also, as you might notice, our `details` have a field named `type`. So here is the list of supported detail types:

| Type | Description |
| :--- | :--- |
| `FIELD_VIOLATION` | Incorrect field value was given |

{% hint style="warning" %}
Details are unordered, so you must rely only on the type
{% endhint %}

### Field violations

Field violation detail shows which field is bad.

It's structure looks something like this:

| Field | Description |
| :--- | :--- |
| `field` | Name of the bad field |
| `message` | What violation is in the field |

{% hint style="info" %}
There might be multiple "field violation" details, each represents it's own request field.
{% endhint %}



