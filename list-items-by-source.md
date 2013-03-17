---
layout: deprecated
title: List Items by Source
categories: items
---

# List Items by Source

Page through all of your items created using a specific application. An item's
`source` is set to the [User-Agent][] used when it was created. Use the `source`
parameter when [listing items](/list-items) to show only those created by a
specific application. See [List Items](/list-items) for recommendations using
this endpoint.

[User-Agent]: http://en.wikipedia.org/wiki/User_agent


## Example

The CloudApp Mac app uses the User-Agent `Cloud/1.5.1` so all items it creates
will have that User-Agent as their `source`. To list only the items created
using the Mac app, use the parameter `source=Cloud`. Get fancy and list only the
items created using a specific version of with `source=Cloud/1.5.1`. Remember
querystring parameters must be [URL encoded][url-encoded] but most HTTP
libraries will handle this for you.

[url-encoded]: http://en.wikipedia.org/wiki/Percent-encoding


## Request

- Requires [authentication](https://github.com/cloudapp/api/blob/master/README.md#authentication)
- HTTP Method: GET
- URL: http://my.cl.ly/items?source=*Cloud*


## Response

- Status: 200 OK
- Body:

      [{
        "href":          "http://my.cl.ly/items/1912729",
        "name":          "My CloudApp",
        "private":       true,
        "subscribed":    false,
        "url":           "http://cl.ly/40b6ab341aca432a34ee",
        "content_url":   "http://cl.ly/40b6ab341aca432a34ee",
        "item_type":     "bookmark",
        "view_counter":  0,
        "icon":          "http://my.cl.ly/images/item_types/bookmark.png",
        "remote_url":    null,
        "redirect_url":  "http://my.cl.ly",
        "source":        "Cloud/1.5.1 CFNetwork/520.0.13 Darwin/11.0.0 (x86_64) (MacBookPro5%2C5)",
        "created_at":    "2010-10-23T20:10:37Z",
        "updated_at":    "2010-10-23T20:10:41Z",
        "deleted_at":    null
      }, {
        "href":          "http://my.cl.ly/items/1912565",
        "name":          "CloudApp",
        "private":       false,
        "subscribed":    false,
        "url":           "http://cl.ly/2wt6",
        "content_url":   "http://cl.ly/2wt6",
        "item_type":     "bookmark",
        "view_counter":  2,
        "icon":          "http://my.cl.ly/images/item_types/bookmark.png",
        "remote_url":    null,
        "redirect_url":  "http://getcloudapp.com",
        "source":        "Cloud/1.5.1 CFNetwork/520.0.13 Darwin/11.0.0 (x86_64) (MacBookPro5%2C5)",
        "created_at":    "2010-10-23T19:50:24Z",
        "updated_at":    "2010-10-23T19:50:39Z",
        "deleted_at":    null
      }, {
        "href":          "http://my.cl.ly/items/1912559",
        "name":          "CloudApp Logo.png",
        "private":       false,
        "subscribed":    false,
        "url":           "http://cl.ly/2wr4",
        "content_url":   "http://cl.ly/2wr4/CloudApp%20Logo.png",
        "item_type":     "image",
        "view_counter":  85,
        "icon":          "http://my.cl.ly/images/new/item-types/image.png",
        "remote_url":    "http://f.cl.ly/items/7c7aea1395c3db0aee18/CloudApp%20Logo.png",
        "thumbnail_url": "http://thumbs.cl.ly/2wr4",
        "redirect_url":  null,
        "source":        "Cloud/1.5.1 CFNetwork/520.0.13 Darwin/11.0.0 (x86_64) (MacBookPro5%2C5)",
        "created_at":    "2010-10-23T19:50:13Z",
        "updated_at":    "2011-04-04T00:33:57Z",
        "deleted_at":    null
      }]

## Example

{: .shell}
    curl --digest -u arthur@dent.com:towel \
         -H "Accept: application/json" \
         "http://my.cl.ly/items?page=1&per_page=5&source=Cloud"
