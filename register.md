---
layout: deprecated
title: Register
categories: account
---

# Register

Create a CloudApp account.


## Request

- HTTP Method: POST
- URL: http://my.cl.ly/register
- Body:

      {
        "user": {
          "email":      "arthur@dent.com",
          "password":   "towel",
          "accept_tos": true
        }
      }


## Response

- Status: 201 Created
- Body:

      {
        "id":               1,
        "email":            "arthur@dent.com",
        "domain":           null,
        "domain_home_page": null,
        "private_items":    true,
        "subscribed":       false,
        "alpha":            false,
        "created_at":       "2010-12-10T17:07:01Z",
        "updated_at":       "2010-12-10T17:07:01Z",
        "activated_at":     "2010-12-10T17:07:01Z"
      }


## Example

{: .shell}
    curl -H "Accept: application/json" \
         -H "Content-Type: application/json" \
         -d \
            '{
              "user": {
                "email":      "arthur@dent.com",
                "password":   "towel",
                "accept_tos": true
              }
            }' \
         http://my.cl.ly/register
