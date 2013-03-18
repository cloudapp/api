# Rename Item

Change the name of an item.

## Request

- Requires [authentication](https://github.com/cloudapp/api/blob/master/README.md#authentication)
- HTTP Method: PUT
- URL: Value of item's `href` attribute. _(e.g., http://my.cl.ly/items/1912565)_
- Body:

  ```js
  {
    "item": {
      "name": "Betelgeuse"
    }
  }
  ```

## Response

- Status: 200 OK
- Body:

  ```js
  {
    "href":         "http://my.cl.ly/items/1912565",
    "name":         "Betelgeuse",
    "private":      false,
    "subscribed":   false,
    "url":          "http://cl.ly/2wt6",
    "content_url":  "http://cl.ly/2wt6",
    "item_type":    "bookmark",
    "view_counter": 0,
    "icon":         "http://my.cl.ly/images/item_types/bookmark.png",
    "remote_url":   null,
    "redirect_url": "http://getcloudapp.com",
    "source":       "Cloud/1.5.1 CFNetwork/520.0.13 Darwin/11.0.0 (x86_64) (MacBookPro5%2C5)",
    "created_at":   "2010-10-23T21:15:21Z",
    "updated_at":   "2010-10-24T01:38:28Z",
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
            "name": "Betelgeuse"
          }
        }' \
     -X PUT \
     "http://my.cl.ly/items/1912565"
```