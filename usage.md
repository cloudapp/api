---
layout: deprecated
title: Usage
categories: basics
---

# Usage

You can use the CloudApp API to [register an account](/register/),
[list your items](/list-items/), [upload a file](/upload-file/) -- anything
[Cloud.app](http://getcloudapp.com/download/) or the [web app](http://my.cl.ly/)
can do. Keep in mind usage of the CloudApp API is bound to our [Terms of
Service](http://getcloudapp.com/terms/).

## Authentication

[HTTP Digest](http://en.wikipedia.org/wiki/Digest_access_authentication) is
used to authenticate all requests.

## JSON

You're probably interested in JSON responses and not HTML. Add the header
`Accept: application/json` on requests to receive JSON and `Content-Type:
application/json` when you're sending JSON.
