# List Drops

Always start by requesting the API root.

```bash
$ curl -i "http://api.getcloudapp.com/"

HTTP/1.1 401 Unauthorized
Cache-Control: no-cache
Content-Type: application/vnd.collection+json; charset=utf-8
Www-Authenticate: Token realm="CloudApp"
{
  "collection" :
  {
    "version"  : "1.0",
    "href"     : "...",
    "template" :
    {
      "data" :
      [
        { "name" : "email",    "value" : null },
        { "name" : "password", "value" : null }
      ]
    }
  }
}
```

[Retrieve the account token](/token) if it hasn't persisted from a previous
request. If the token is saved, add it to the `Authorization` header in the
format `Token token="<value>"` and follow the `root` link.

```bash
$ curl -i -H 'Authorization: Token token="0gc504cf7e4a51ff8119"' \
       "http://api.getcloudapp.com/"

HTTP/1.1 200 OK
Cache-Control: must-revalidate, private, max-age=0
Content-Type: application/vnd.collection+json; charset=utf-8
Etag: "ebdf7b114b2f1575a69b1cc2e58082e5"
{
  "collection" :
  {
    "version" : "1.0",
    "href"    : "...",
    "links"   :
    [
      { "rel" : "drops", "href" : "..." }
    ]
  }
}
```

Follow the `drops` link.

```bash
$ curl -i -H 'Authorization: Token token="0gc504cf7e4a51ff8119"' \
       "http://api.getcloudapp.com/drops"

HTTP/1.1 200 OK
Cache-Control: must-revalidate, private, max-age=0
Content-Type: application/vnd.collection+json; charset=utf-8
Etag: "4325a48a603b06f9f46ab5312e2df849"
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
        "rel"  : "drops-list",
        "href" : "...",
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
    }
  }
}
```

Following [the Collection+JSON spec][queries], submit the `drops-list` query
template. Fill in the `time_zone` parameter using an
[identifier from the IANA time zone database][time-zone].

[queries]:   http://amundsen.com/media-types/collection/format/#query-templates
[time-zone]: http://en.wikipedia.org/wiki/IANA_time_zone_database

```bash
$ curl -i -H 'Authorization: Token token="0gc504cf7e4a51ff8119"' \
       --get \
       --data filter=active \
       --data limit=20 \
       --data time_zone=America/New_York \
       "http://api.getcloudapp.com/drops"

HTTP/1.1 200 OK
Cache-Control: must-revalidate, private, max-age=0
Content-Type: application/vnd.collection+json; charset=utf-8
Etag: "4325a48a603b06f9f46ab5312e2df849"
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
      },
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
          { "name" : "id",       "value" : 19225845 },
          { "name" : "name",     "value" : "Image 2012-06-12 at 3.08.57 PM.png" },
          { "name" : "private",  "value" : true },
          { "name" : "trash",    "value" : false },
          { "name" : "views",    "value" : 4 },
          { "name" : "created",  "value" : "2012-06-12T19:08:54Z" },
          { "name" : "grouping", "value" : "Today" }
        ]
      }
    ]
  }
}
```

Follow the `next` and `previous` links to paginate through the drops collection.

```bash
$ curl -i -H 'Authorization: Token token="0gc504cf7e4a51ff8119"' \
       "http://api.getcloudapp.com/drops?page=2&per_page=20"

HTTP/1.1 200 OK
Content-Type: application/vnd.collection+json; charset=utf-8
ETag: "ba401fa75b322ee994b109805871855c"
Cache-Control: max-age=0, private, must-revalidate
{
  "collection" :
  {
    "version" : "1.0",
    "href"    : "...",
    "links"   :
    [
      { "rel" : "next",     "href" : "..." },
      { "rel" : "previous", "href" : "..." }
    ],
    "template" : {...},
    "items"    : [...]
  }
}
```