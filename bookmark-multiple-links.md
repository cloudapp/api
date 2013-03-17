---
layout: deprecated
title: Bookmark Multiple Links
categories: items
---

# Bookmark Multiple Links

Create multiple bookmarks in a single request.


## Request

- Requires [authentication](https://github.com/cloudapp/api/blob/master/README.md#authentication)
- HTTP Method: POST
- URL: http://my.cl.ly/items
- Body:

      {
        "items": [{
          "name":         "Authur Dent",
          "redirect_url": "http://en.wikipedia.org/wiki/Arthur_Dent"
        }, {
          "name":         "Ford Prefect",
          "redirect_url": "http://en.wikipedia.org/wiki/Ford_Prefect_(character)"
        }, {
          "name":         "Zaphod Beeblebrox",
          "redirect_url": "http://en.wikipedia.org/wiki/Zaphod_Beeblebrox"
        }]
      }


## Response

Returns an array containing each item created.

- Status: 200 OK
- Body:

      [{
        "href":         "http://my.cl.ly/items/2571666",
        "name":         "Authur Dent",
        "private":      true,
        "subscribed":   false,
        "url":          "http://cl.ly/0W2l1e421F3W17011z0M",
        "content_url":  "http://cl.ly/0W2l1e421F3W17011z0M",
        "item_type":    "bookmark",
        "view_counter": 0,
        "icon":         "http://my.cl.ly/images/item_types/bookmark.png",
        "remote_url":   null,
        "redirect_url": "http://en.wikipedia.org/wiki/Arthur_Dent",
        "source":       "Cloud/1.5.1 CFNetwork/520.0.13 Darwin/11.0.0 (x86_64) (MacBookPro5%2C5)",
        "created_at":   "2010-12-15T14:21:55Z",
        "updated_at":   "2010-12-15T14:21:55Z",
        "deleted_at":   null,
      }, {
        "href":         "http://my.cl.ly/items/2571696",
        "name":         "Ford Prefect",
        "private":      true,
        "subscribed":   false,
        "url":          "http://cl.ly/1f0t1k1X3a3B053b0w0U",
        "content_url":  "http://cl.ly/1f0t1k1X3a3B053b0w0U",
        "item_type":    "bookmark",
        "view_counter": 0,
        "icon":         "http://my.cl.ly/images/item_types/bookmark.png",
        "remote_url":   null,
        "redirect_url": "http://en.wikipedia.org/wiki/Ford_Prefect_(character)",
        "source":       "Cloud/1.5.1 CFNetwork/520.0.13 Darwin/11.0.0 (x86_64) (MacBookPro5%2C5)",
        "created_at":   "2010-12-15T14:21:55Z",
        "updated_at":   "2010-12-15T14:21:55Z",
        "deleted_at":   null
      }, {
        "href":         "http://my.cl.ly/items/2571715",
        "name":         "Zaphod Beeblebrox",
        "private":      true,
        "subscribed":   false,
        "url":          "http://cl.ly/153K342u2Q2l1n0u340K",
        "content_url":  "http://cl.ly/153K342u2Q2l1n0u340K",
        "item_type":    "bookmark",
        "view_counter": 0,
        "icon":         "http://my.cl.ly/images/item_types/bookmark.png",
        "remote_url":   null,
        "redirect_url": "http://en.wikipedia.org/wiki/Zaphod_Beeblebrox",
        "source":       "Cloud/1.5.1 CFNetwork/520.0.13 Darwin/11.0.0 (x86_64) (MacBookPro5%2C5)",
        "created_at":   "2010-12-15T14:21:55Z",
        "updated_at":   "2010-12-15T14:21:55Z",
        "deleted_at":   null
      }]


## Example

{: .shell}
    curl --digest -u arthur@dent.com:towel \
         -H "Accept: application/json" \
         -H "Content-Type: application/json" \
         -d \
           '{
              "items": [{
                "name":         "Authur Dent",
                "redirect_url": "http://en.wikipedia.org/wiki/Arthur_Dent"
              }, {
                "name":         "Ford Prefect",
                "redirect_url": "http://en.wikipedia.org/wiki/Ford_Prefect_(character)"
              }, {
                "name":         "Zaphod Beeblebrox",
                "redirect_url": "http://en.wikipedia.org/wiki/Zaphod_Beeblebrox"
              }]
           }' \
         "http://my.cl.ly/items"


## Errors

If a bookmark is unable to be created, its place in the array will be an array of error messages.

- Status: 422 Unprocessable Entity
- Body:

      [{
        "href":         "http://my.cl.ly/items/2571666",
        "name":         "Authur Dent",
        "private":      true,
        "subscribed":   false,
        "url":          "http://cl.ly/0W2l1e421F3W17011z0M",
        "content_url":  "http://cl.ly/0W2l1e421F3W17011z0M",
        "item_type":    "bookmark",
        "view_counter": 0,
        "icon":         "http://my.cl.ly/images/item_types/bookmark.png",
        "remote_url":   null,
        "redirect_url": "http://en.wikipedia.org/wiki/Arthur_Dent",
        "source":       "Cloud/1.5.1 CFNetwork/520.0.13 Darwin/11.0.0 (x86_64) (MacBookPro5%2C5)",
        "created_at":   "2010-12-15T14:21:55Z",
        "updated_at":   "2010-12-15T14:21:55Z",
        "deleted_at":   null,
      }, [
        "URL can't be blank"
      ], {
        "href":         "http://my.cl.ly/items/2571715",
        "name":         "Zaphod Beeblebrox",
        "private":      true,
        "subscribed":   false,
        "url":          "http://cl.ly/153K342u2Q2l1n0u340K",
        "content_url":  "http://cl.ly/153K342u2Q2l1n0u340K",
        "item_type":    "bookmark",
        "view_counter": 0,
        "icon":         "http://my.cl.ly/images/item_types/bookmark.png",
        "remote_url":   null,
        "redirect_url": "http://en.wikipedia.org/wiki/Zaphod_Beeblebrox",
        "source":       "Cloud/1.5.1 CFNetwork/520.0.13 Darwin/11.0.0 (x86_64) (MacBookPro5%2C5)",
        "created_at":   "2010-12-15T14:21:55Z",
        "updated_at":   "2010-12-15T14:21:55Z",
        "deleted_at":   null
      }]
