---
layout: deprecated
title: View Item
categories: items
---

# View Item

Get metadata about a cl.ly URL like name, type, or view count.

## Request

- HTTP Method: GET
- URL: Value of `url` on an item. _(e.g., http://cl.ly/2wr4)_

## Response

- Status: 200 OK
- Body:

      {
        "href":          "http://my.cl.ly/items/1912559",
        "name":          "CloudApp Logo.png",
        "private":       false,
        "subscribed":    false,
        "url":           "http://cl.ly/2wr4",
        "content_url":   "http://cl.ly/2wr4/CloudApp%20Logo.png",
        "item_type":     "image",
        "view_counter":  42,
        "icon":          "http://my.cl.ly/images/new/item-types/image.png",
        "remote_url":    "http://f.cl.ly/items/7c7aea1395c3db0aee18/CloudApp%20Logo.png",
        "thumbnail_url": "http://thumbs.cl.ly/2wr4",
        "redirect_url":  null,
        "source":        "Cloud/1.5.1 CFNetwork/520.0.13 Darwin/11.0.0 (x86_64) (MacBookPro5%2C5)",
        "created_at":    "2010-10-23T19:50:13Z",
        "updated_at":    "2010-10-23T19:50:38Z",
        "deleted_at":    null
      }


## Example

{: .shell}
    curl -H "Accept: application/json" http://cl.ly/2wr4
