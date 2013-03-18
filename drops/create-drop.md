# Create Drop

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
       'http://api.getcloudapp.com/'

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
       'http://api.getcloudapp.com/drops'

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

# Bookmark a Link

Following [the Collection+JSON spec][template], fill `template` with the drop's
name and URL to bookmark. Send it as an HTTP POST to the collection's `href`.
**Note:** The value of the `private` field will be the default drop privacy the
owner has configured for their account.

**TODO:** This resource MUST accept `application/vnd.collection+json` as per the
Collection+JSON spec.

[template]: http://amundsen.com/media-types/collection/format/#adding-items

```bash
$ curl -i 'Authorization: Token token="0gc504cf7e4a51ff8119"' \
       -X POST \
       -d 'name=CloudApp' \
       -d 'private=true' \
       -d 'trash=false' \
       -d 'bookmark_url=http://getcloudapp.com' \
       -d 'file_size=' \
       'http://api.getcloudapp.com/drops'

HTTP/1.1 201 Created
Cache-Control: max-age=0, private, must-revalidate
Content-Type: application/vnd.collection+json; charset=utf-8
Etag: "9210a8f3c5ce5937159ddac0fc95f81a"
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
          { "rel" : "collection", "href" : "..." },
          { "rel" : "canonical",  "href" : "..." },
          { "rel" : "icon",       "href" : "..." }
        ],
        "data" :
        [
          { "name" : "id",       "value" : 19265445 },
          { "name" : "name",     "value" : "CloudApp" },
          { "name" : "private",  "value" : true },
          { "name" : "trash",    "value" : false },
          { "name" : "views",    "value" : 0 },
          { "name" : "created",  "value" : "2012-06-13T18:53:52Z" },
          { "name" : "grouping", "value" : "Today" }
        ]
      }
    ]
  }
}
```

# Upload a File

Following [the Collection+JSON spec][template], fill `template` with the drop's
name and the size in bytes of the file to be uploaded. Send it as an HTTP POST
to the collection's `href`. **Note:** The value of the `private` field will be
the default drop privacy the owner has configured for their account.

**TODO:** This resource MUST accept `application/vnd.collection+json` as per the
Collection+JSON spec.

[template]: http://amundsen.com/media-types/collection/format/#adding-items

```bash
$ curl -i -H 'Authorization: Token token="0gc504cf7e4a51ff8119"' \
       -X POST \
       -d 'name=' \
       -d 'private=true' \
       -d 'trash=false' \
       -d 'bookmark_url=' \
       -d 'file_size=1150' \
       'http://api.getcloudapp.com/drops'

HTTP/1.1 201 Created
Cache-Control: max-age=0, private, must-revalidate
Content-Type: application/vnd.collection+json; charset=utf-8
Etag: "223d43361131cb12dcdc075ca48a9aaf"
{
  "collection" :
  {
    "version"  : "1.0",
    "href"     : "...",
    "template" :
    {
      "enctype" : "multipart/form-data",
      "data"    :
      [
        { "name" : "success_action_redirect", "value" : "http://api.getcloudapp.com/..." },
        { "name" : "AWSAccessKeyId", "value" : "AKIAIDPUZISHSBEOFS6Q" },
        { "name" : "key",            "value" : "items/422X1J3J020J1Z1S0V19/${filename}" },
        { "name" : "policy",         "value" : "eyJleHBpcmF0aW9uIjoiMjAxM..." },
        { "name" : "signature",      "value" : "0zsDbT0t8hRkyHfWj2MTo0Ot6ec=" },
        { "name" : "acl",            "value" : "public-read" },
        { "name" : "file",           "value" : null }
      ]
    },
    "items" :
    [
      {
        "href"  : "...",
        "links" :
        [
          { "rel" : "collection", "href" : "..." },
          { "rel" : "canonical",  "href" : "..." },
          { "rel" : "icon",       "href" : "..." }
        ],
        "data" :
        [
          { "name" : "id",       "value" : 19265445 },
          { "name" : "name",     "value" : "CloudApp" },
          { "name" : "private",  "value" : true },
          { "name" : "trash",    "value" : false },
          { "name" : "views",    "value" : 0 },
          { "name" : "created",  "value" : "2012-06-13T18:53:52Z" },
          { "name" : "grouping", "value" : "Today" }
        ]
      }
    ]
```

Fill `template` with the file to be uploaded. Encode each name and value pair in
`data` as `multipart/form-data` and POST it to the collection's `href`. The
server will respond with a `303 See Other` redirect which MUST be followed to
complete the upload process.

**Note:** According to [Amazon's documentation][s3-docs], any parameter after
`file` is ignored. Make sure `file` is the last parameter in the encoded request
or the upload may be rejected.

[s3-docs]: http://developer.amazonwebservices.com/connect/entry.jspa?externalID=1434

```bash
$ curl -iL \
       -F 'success_action_redirect=https://api.getcloudapp.com/...' \
       -F 'AWSAccessKeyId=AKIAIDPUZISHSBEOFS6Q' \
       -F 'key=items/3N2I1J3u310m3k2j1K1M/${filename}' \
       -F 'policy=eyJleHBpcmF0aW9uIjoiMjAxM...' \
       -F 'signature=/4Sppkaz9JAXup9Q8tLcdWoW51M=' \
       -F 'acl=public-read' \
       -F 'file=@/Users/Larry/Desktop/favicon.ico' \
       'http://f.cl.ly'

HTTP/1.1 100 Continue

HTTP/1.1 303 See Other
ETag: "567d2d49d2d30e2db956d680a4d03f25"
Location: https://api.getcloudapp.com/drops/19266622/s3?token=0gc504cf7e4a51ff8119&bucket=f.cl.ly&key=items%2F3N2I1J3u310m3k2j1K1M%2Ffavicon.ico&etag=%22567d2d49d2d30e2db956d680a4d03f25%22

HTTP/1.1 200 OK
Cache-Control: max-age=0, private, must-revalidate
Content-Type: application/vnd.collection+json; charset=utf-8
Etag: "ab14d10bc6c3d317b4921f9205256546"
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
          { "rel" : "collection", "href" : "..." },
          { "rel" : "canonical",  "href" : "..." },
          { "rel" : "icon",       "href" : "..." },
          { "rel" : "embed",      "href" : "..." },
          { "rel" : "download",   "href" : "..." }
        ],
        "data" :
        [
          { "name" : "id",       "value" : 19266622 },
          { "name" : "name",     "value" : "favicon.ico" },
          { "name" : "private",  "value" : true },
          { "name" : "trash",    "value" : false },
          { "name" : "views",    "value" : 0 },
          { "name" : "created",  "value" : "2012-06-13T18:53:52Z" },
          { "name" : "grouping", "value" : "Today" }
        ]
      }
    ]
  }
}
```