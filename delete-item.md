---
layout: deprecated
title: Delete Item
categories: items
---

# Delete Item

Send an item to the trash.

## Request

- Requires [authentication](https://github.com/cloudapp/api/blob/master/README.md#authentication)
- HTTP Method: DELETE
- URL: Value of item's `href` attribute. _(e.g., http://my.cl.ly/items/1912565)_

## Response

- Status: 200 OK
- Body:

      {
        "href":         "http://my.cl.ly/items/1912565",
        "name":         "CloudApp",
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
        "updated_at":   "2010-10-23T21:17:04Z",
        "deleted_at":   "2010-10-25T14:37:43Z"
      }


## Example

{: .shell}
    curl --digest -u arthur@dent.com:towel \
         -H "Accept: application/json" \
         -X DELETE \
         "http://my.cl.ly/items/1912565"
