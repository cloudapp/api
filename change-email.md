---
layout: deprecated
title: Change Email
categories: account
---

# Change Email

Change the email address for an account.


## Request

- Requires [authentication](https://github.com/cloudapp/api/blob/master/README.md#authentication) and current password
- HTTP Method: PUT
- URL: http://my.cl.ly/account
- Body:

      {
        "user": {
          "email":            "ford@prefect.com",
          "current_password": "towel",
        }
      }


## Response

- Status: 200 OK
- Body:

      {
        "id":               1,
        "email":            "ford@prefect.com",
        "domain":           null,
        "domain_home_page": null,
        "private_items":    true,
        "subscribed":       false,
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
                "email":            "ford@prefect.com",
                "current_password": "towel"
              }
            }' \
         -X PUT \
         "http://my.cl.ly/account"
