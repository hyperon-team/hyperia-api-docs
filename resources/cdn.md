---
description: >-
  CDN is a very important part for any media-related project. It hosts all the
  data, images and such stuff. Here is explained how to use it and what
  endpoints it has.
---

# CDN

### Supported image formats

{% hint style="info" %}
Currently the CDN will discard any image format, leaving only `Content-Type` to indicate it.
{% endhint %}

* JPG
* WEBP
* GIF
* PNG

### Endpoints

| Name                  | Path                                  |
| --------------------- | ------------------------------------- |
| Custom community icon | icons/[community\_id](communities.md) |
| Custom user avatar    | avatar/[user\_id](users.md)           |
| Default user avatar   | embed/avatar.svg                      |

