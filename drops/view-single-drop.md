# View Single Drop

Follow a drop's `href` from the [drops collection](/list-drops).

```bash
$ curl -i -H 'Authorization: Token token="0gc504cf7e4a51ff8119"' \
       "http://api.getcloudapp.com/drops/13950097"

HTTP/1.1 200 OK
Cache-Control: must-revalidate, private, max-age=0
Content-Type: application/vnd.collection+json; charset=utf-8
Etag: "31015634cc7f3718fbaff3718a4dd25f"
{
  "collection" :
  {
    "version" : "1.0",
    "href"    : "...",
    "links" :
    [
      { "rel" : "drops-stream", "href" : "..." }
    ],
    "queries" :
    [
      {
        "href" : "...",
        "rel"  : "drops-list",
        "data" :
        [
          { "name" : "filter",    "value" : "active" },
          { "name" : "limit",     "value" : 20 },
          { "name" : "time_zone", "value" : "UTC" }
        ]
      }
    ],
    "template" :
    {
      "data" :
      [
        { "name" : "name",         "value" : null },
        { "name" : "private",      "value" : true },
        { "name" : "trash",        "value" : false },
        { "name" : "bookmark_url", "value" : null },
        { "name" : "file_size",    "value" : null }
      ]
    },
    "items" :
    [
      {
        "href"  : "...",
        "links" :
        [
          { "rel" : "root",       "href" : "..." },
          { "rel" : "collection", "href" : "..." },
          { "rel" : "canonical",  "href" : "..." },
          { "rel" : "icon",       "href" : "..." },
          { "rel" : "embed",      "href" : "..." },
          { "rel" : "download",   "href" : "..." }
        ],
        "data" :
        [
          { "name" : "id",       "value" : 19225923 },
          { "name" : "name",     "value" : "Chapter 1.md" },
          { "name" : "private",  "value" : true },
          { "name" : "trash",    "value" : false },
          { "name" : "views",    "value" : 0 },
          { "name" : "created",  "value" : "2012-06-12T19:10:44Z" },
          { "name" : "grouping", "value" : "Today" }
        ]
      }
    ]
  }
}
```