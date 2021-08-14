---
description: List of error codes with their status code and description
---

# Opcodes and status codes

## JSON error codes

| Error code | Status code | Description |
| :--- | :--- | :--- |
| `OK` | 200 | Everything is ok, request was successful |
| `MISSING_ACCESS` | 403 | You lack permissions to access the endpoint/perform the operation |
| `NOT_IMPLEMENTED` | 501 | The endpoint or functional not implemented |
| `BAD_REQUEST` | 400 | Invalid data \(syntax, value errors\) was sent |
| `INTERNAL` | 500 | Internal error happened |
| `UNKNOWN_USER` | 404 | System cannot identify the user |
| `UNKNOWN_COMMUNITY` | 404 | System cannot identify the community |
| `NO_UPDATE_PERMISSION` | 403 | You lack permissions to update the community or user |
| `AUTHENTICATED_USER_NOT_EXISTS` | 401 | User to whom the access was issued does not longer exist |
| `INVALID_CREDENTIALS` | 401 | Invalid authentication credentials was sent |
| `INVALID_TOKEN_PAIR` | 401 | Invalid token pair was provided |
| `CONNECTION_PROVIDER_NOT_SUPPORTED` | 501 | Specified connection provider is not supported |
| `CONNECTION_ALREADY_EXISTS` | 409 | Such connection already exists for the user |
| `CONNECTION_NOT_FOUND` | 404 | System cannot identify the connection |
| `INCOMPATIBLE_CONNECTION_DATA` | 400 | Incompatible connection data was sent \(e.g. provider - oauth2, data - login & password\) |
| `NICK_IS_TAKEN` | 409 | Specified user nickname is already taken by someone else |
| `CANNOT_CHANGE_USER_PASSWORD` | 403 | This error happens if user with update permission tries to lock user out of his account by changing password |
| `CANNOT_CHANGE_USER_PERMISSIONS` | 403 | You lack permissions to change other user's permissions |

