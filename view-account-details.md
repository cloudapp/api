# View Account Details

Get the basic details of the authenticated account. This is the same response as
returned by most account endpoints.

## Request

- Requires [authentication](https://github.com/cloudapp/api/blob/master/README.md#authentication)
- HTTP Method: GET
- URL: http://my.cl.ly/account

## Response

- Status: 200 OK
- Body:

  ```js
  {
    "id":                      1,
    "email":                   "arthur@dent.com",
    "domain":                  null,
    "domain_home_page":        null,
    "private_items":           true,
    "subscribed":              true,
    "subscription_expires_at": "2012-05-21",
    "alpha":                   false,
    "created_at":              "2011-04-21T23:07:52Z",
    "updated_at":              "2011-04-21T23:07:52Z",
    "activated_at":            "2011-04-21T23:07:52Z",
    "socket": {
      "auth_url": "http://my.cl.ly/pusher/auth",
      "api_key":  "36b8e92a50487f79cbb3",
      "app_id":   "4072",
      "channels": {
        "items": "private-items_1"
      }
    }
  }
  ```

## Example

```bash
curl --digest -u arthur@dent.com:towel \
     -H "Accept: application/json" \
     "http://my.cl.ly/account"
```