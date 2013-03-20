# Drops Pagination

_**TODO:** Describe drops pagination._

```
{
  "collection": {
    "href": "http://api.getcloudapp.dev/drops",
    "links": [
      { "rel": "first", "href": "http://api.getcloudapp.dev/drops?filter=active&per_page=20" },
      { "rel": "previous", "href": "http://api.getcloudapp.dev/drops?filter=active&page=1&per_page=20" },
      { "rel": "next", "href": "http://api.getcloudapp.dev/drops?filter=active&page=3&per_page=20" },
      { "rel": "next-stream", "href": "http://api.getcloudapp.dev/drops?drop_id=451&filter=active&per_page=20" }
    ],
    "template": {
      "data": [
        { "name": "name", "value": null },
        { "name": "private", "value": true },
        { "name": "trash", "value": false },
        { "name": "bookmark_url", "value": null },
        { "name": "file_size", "value": null }
      ]
    },
    "queries": [
      {
        "rel": "filter-drops",
        "href": "http://api.getcloudapp.dev/drops",
        "data": [
          { "name": "types", "prompt": "Types" },
          { "name": "limit", "prompt": "Drops Per Page", "value": 20 }
        ]
      }
    ],
    "items": [
      {
        "href": "http://api.getcloudapp.dev/drops/475",
        "links": [
          { "rel": "collection", "href": "http://api.getcloudapp.dev/drops" },
          { "rel": "canonical", "href": "http://cl.dev/1V0i1V2V0p0F" },
          { "rel": "icon", "href": "https://secure.assets.my.cl.dev/images/thumbnails/unknown.png" }
        ],
        "data": [
          { "name": "id", "value": 475 },
          { "name": "name", "value": null },
          { "name": "private", "value": true },
          { "name": "trash", "value": false },
          { "name": "views", "value": 0 },
          { "name": "created", "value": "2013-01-03T16:54:22Z" }
        ]
      },
      ...
      {
        "href": "http://api.getcloudapp.dev/drops/451",
        "links": [
          { "rel": "collection", "href": "http://api.getcloudapp.dev/drops" },
          { "rel": "canonical", "href": "http://cl.dev/3S0Z0B1a0D1u" },
          { "rel": "icon", "href": "https://secure.assets.my.cl.dev/images/thumbnails/unknown.png" }
        ],
        "data": [
          { "name": "id", "value": 451 },
          { "name": "name", "value": null },
          { "name": "private", "value": true },
          { "name": "trash", "value": false },
          { "name": "views", "value": 0 },
          { "name": "created", "value": "2012-12-13T19:06:27Z" }
        ]
      }
    ],
    "version": "1.0"
  }
}
```
