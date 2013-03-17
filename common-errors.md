---
layout: deprecated
title: Common Errors
categories: basics
---

# Common Errors

There are several errors that may be returned by any CloudApp API endpoint.
These are their stories.


## Unactivated Account

Using CloudApp requires an activated account. Upon registering for an account, a
link is emailed that must be clicked to confirm ownership of the email address.
Nothing particularly surprising.

One difference from other systems is CloudApp offers an activation grace period.
An unactivated account may be used before the activation restriction is put into
effect. This allows someone to register for an account using the Mac or web apps
and use it immediately without having to bounce back and forth between CloudApp
and their inbox.

After the activation restriction takes effect, authenticated requests for an
unactivated account will return the following response:

- Status: 409 Conflict
- Body:

      [ "Your account hasn't been activated. Please check your email and activate your account." ]
