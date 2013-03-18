# Bookmark Link

Create a bookmark to a URL.

## Request

- Requires [authentication](https://github.com/cloudapp/api/blob/master/README.md#authentication)
- HTTP Method: POST
- URL: http://my.cl.ly/items
- Body:

  ```js
  {
    "item": {
      "name":         "CloudApp",
      "redirect_url": "http://getcloudapp.com"
    }
  }
  ```

## Response

- Status: 200 OK
- Body:

  ```js
  {
    "href":         "http://my.cl.ly/items/4257111",
    "name":         "CloudApp",
    "private":      true,
    "subscribed":   false,
    "url":          "http://cl.ly/3f3z1a303l2W1I2h2e3a",
    "content_url":  "http://cl.ly/3f3z1a303l2W1I2h2e3a",
    "item_type":    "bookmark",
    "view_counter": 0,
    "icon":         "http://my.cl.ly/images/new/item-types/bookmark.png",
    "remote_url":   null,
    "redirect_url": "http://getcloudapp.com",
    "source":       "Cloud/1.5.1 CFNetwork/520.0.13 Darwin/11.0.0 (x86_64) (MacBookPro5%2C5)",
    "created_at":   "2010-10-23T19:50:24Z",
    "updated_at":   "2010-10-23T19:50:39Z",
    "deleted_at":   null
  }
  ```

## Example

```bash
curl --digest -u arthur@dent.com:towel \
     -H "Accept: application/json" \
     -H "Content-Type: application/json" \
     -d \
       '{
         "item": {
            "name":         "CloudApp",
            "redirect_url": "http://getcloudapp.com"
         }
       }' \
     "http://my.cl.ly/items"
```

## Errors

There may be one or more errors preventing the bookmark from being created. If
that's the case, the following response will be returned:

- Status: 422 Unprocessable Entity
- Body:

  ```js
  [ "URL can't be blank" ]
  ```