---
description: Page where it all begins...
---

# Intro

Welcome to [Hyperia](https://hyperia.space) API documentation. Hyperia is a smart community advertisement platform.

### Endpoints

Our API is divided into resources (aka services):

* Communities
* Users
* Authentication/Authorization (`auth`)

Each of the services has it's own API version, so you can easily switch between the versions you need.

To make a request to a service you need to specify the name of the service followed by it's version. For example: `/communities/v1` is a valid prefix `/communities` and `/v1/communities` are not.
