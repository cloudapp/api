# Authentication

Authenticate by passing an account's token in the `Authorization` HTTP header.
Exchange account credentials for a token by making an HTTP Basic request to
the authenticate URL. The response will be an [account representation](TODO).

```bash
$ curl -i -u arthur@dent.com http://api.getcloudapp.dev/authorization
Enter host password for user 'arthur@dent.com':
```

```
HTTP/1.1 200 OK
Content-Type: application/vnd.collection+json; charset=utf-8
X-UA-Compatible: IE=Edge
ETag: "9aef6ed7b50536a791241b715cf1a19a"
Cache-Control: max-age=0, private, must-revalidate
Set-Cookie: user_credentials=217a83eadcb6ceb1085b10cc559bfcc752e8f350fbdd626059393f5eeffd8412d5b250f0bc8d457241cb7667b1c8ea070d251edefadb74ee179eef1b1516d74a%3A%3A2; path=/; expires=Tue, 18-Jun-2013 16:38:49 GMT
Set-Cookie: _engine_session=BAh7CEkiD3Nlc3Npb25faWQGOgZFRkkiJTQxZGMzMDRhMmJlNmY4YzdiYzUxNTA3Zjc5NTg1NTJmBjsAVEkiFXVzZXJfY3JlZGVudGlhbHMGOwBGSSIBgDIxN2E4M2VhZGNiNmNlYjEwODViMTBjYzU1OWJmY2M3NTJlOGYzNTBmYmRkNjI2MDU5MzkzZjVlZWZmZDg0MTJkNWIyNTBmMGJjOGQ0NTcyNDFjYjc2NjdiMWM4ZWEwNzBkMjUxZWRlZmFkYjc0ZWUxNzllZWYxYjE1MTZkNzRhBjsAVEkiGHVzZXJfY3JlZGVudGlhbHNfaWQGOwBGaQc%3D--6813722012807df4ae76c5bb00e432b807bea35f; path=/; HttpOnly
X-Runtime: 0.338998
Connection: close

{
  "collection": {
    "href": "https://api.getcloudapp.dev/account",
    "template": {
      "data": [
        { "name": "email", "value": "arthur@dent.com" },
        { "name": "password", "value": null }
      ]
    },
    "items": [
      {
        "href": "https://api.getcloudapp.dev/account",
        "data": [
          { "name": "id", "value": 2 },
          { "name": "email", "value": "arthur@dent.com" },
          { "name": "token", "value": "abc123" },
          { "name": "registered", "value": "2011-12-14T21:56:50Z" },
          { "name": "domain", "value": "localhost:5000" },
          { "name": "pro_expiration", "value": "2013-03-23" }
        ]
      }
    ],
    "links": [
      { "rel": "drops", "href": "https://api.getcloudapp.dev/drops" },
      { "rel": "drops-template", "href": "https://api.getcloudapp.dev/drops/template" },
      { "rel": "stream", "href": "https://api.getcloudapp.dev/drops/stream" },
      { "rel": "store", "href": "http://cremin-group9319.myshopify.com/cart?email=arthur%40dent.com" }
    ],
    "version": "1.0"
  }
}
```

Add the account token to the `Authorization` header and follow the desired
link.

```bash
$ curl -i -H 'Authorization: Token token="abc123"' http://api.getcloudapp.dev/drops
```

```
HTTP/1.1 200 OK
Content-Type: application/vnd.collection+json; charset=utf-8
X-UA-Compatible: IE=Edge
ETag: "f6913ab78fa212bc722db53d756d71f7"
Cache-Control: max-age=0, private, must-revalidate
X-Runtime: 0.389080
Connection: close

{
  "collection": {
    "href": "http://api.getcloudapp.dev/drops",
    "links": [
      { "rel": "next", "href": "http://api.getcloudapp.dev/drops?filter=active&page=2&per_page=20" },
      { "rel": "next-stream", "href": "http://api.getcloudapp.dev/drops?drop_id=490&filter=active&per_page=20" }
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
        "href": "http://api.getcloudapp.dev/drops/509",
        "links": [
          { "rel": "collection", "href": "http://api.getcloudapp.dev/drops" },
          { "rel": "canonical", "href": "http://localhost:5000/image/2n1p1F2p3l2x" },
          { "rel": "icon", "href": "https://secure.assets.my.cl.dev/images/thumbnails/unknown.png" }
        ],
        "data": [
          { "name": "id", "value": 509 },
          { "name": "name", "value": "scout.jpeg" },
          { "name": "private", "value": true },
          { "name": "trash", "value": false },
          { "name": "views", "value": 1 },
          { "name": "created", "value": "2013-01-11T19:22:17Z" }
        ]
      },
      ...
      {
        "href": "http://api.getcloudapp.dev/drops/490",
        "links": [
          { "rel": "collection", "href": "http://api.getcloudapp.dev/drops" },
          { "rel": "canonical", "href": "http://localhost:5000/0U3E470t3U2q" },
          { "rel": "icon", "href": "https://secure.assets.my.cl.dev/images/thumbnails/bookmark.png" }
        ],
        "data": [
          { "name": "id", "value": 490 },
          { "name": "name", "value": "http://google.com" },
          { "name": "private", "value": true },
          { "name": "trash", "value": false },
          { "name": "views", "value": 0 },
          { "name": "created", "value": "2013-01-11T19:03:38Z" }
        ]
      }
    ],
    "version": "1.0"
  }
}
```
