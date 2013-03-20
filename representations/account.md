# Account Representation

_**TODO:** Describe an account representation._

```
{
  "collection": {
    "href": "http://api.getcloudapp.dev/account",
    "template": {
      "data": [
        { "name": "email", "value": "arthur@dent.com" },
        { "name": "password", "value": null }
      ]
    },
    "items": [
      {
        "href": "http://api.getcloudapp.dev/account",
        "data": [
          { "name": "id", "value": 2 },
          { "name": "email", "value": "arthur@dent.com" },
          { "name": "token", "value": "abc123" },
          { "name": "registered", "value": "2011-12-14T21:56:50Z" },
          { "name": "pro_expiration", "value": "2013-03-23" }
        ]
      }
    ],
    "links": [
      { "rel": "drops", "href": "http://api.getcloudapp.dev/drops" },
      { "rel": "drops-template", "href": "http://api.getcloudapp.dev/drops/template" },
      { "rel": "stream", "href": "http://api.getcloudapp.dev/drops/stream" },
      { "rel": "store", "href": "http://cremin-group9319.myshopify.com/cart?email=arthur%40dent.com" }
    ],
    "version": "1.0"
  }
}
```
