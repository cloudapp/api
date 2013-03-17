---
layout: deprecated
title: Set Custom Domain
categories: account
---

# Set Custom Domain

If the account has a CloudApp Pro subscription, add or change the domain used for all links. Optionally, a URL may be provided to redirect visitors to the custom domain's root.


## Request

- Requires [authentication](https://github.com/cloudapp/api/blob/master/README.md#authentication)
- HTTP Method: PUT
- URL: http://my.cl.ly/account
- Body:

      {
        "user": {
          "domain":           "dent.com",
          "domain_home_page": "http://hhgproject.org"
        }
      }


## Response

- Status: 200 OK
- Body:

      {
        "id":               1,
        "email":            "arthur@dent.com",
        "domain":           "dent.com",
        "domain_home_page": "http://hhgproject.org",
        "private_items":    true,
        "subscribed":       true,
        "alpha":            false,
        "created_at":       "2010-12-10T17:07:01Z",
        "updated_at":       "2010-12-10T20:33:38Z",
        "activated_at":     "2010-12-10T17:07:01Z"
      }


## Example

{: .shell}
    curl --digest -u arthur@dent.com:towel \
         -H "Accept: application/json" \
         -H "Content-Type: application/json" \
         -d \
           '{
              "user": {
                "domain":           "dent.com",
                "domain_home_page": "http://hhgproject.org"
              }
            }' \
         -X PUT \
         "http://my.cl.ly/account"


## Errors

If the domain or domain home page are unable to be added, an array of errors
will be returned.

- Status: 422 Unprocessable Entity
- Body:

      [ "Domain requires a paid plan" ]
