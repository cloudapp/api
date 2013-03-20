# Upload Representation

_**TODO:** Describe an upload representation._

```
{
  "collection": {
    "href": "http://dev.f.cl.ly",
    "template": {
      "enctype": "multipart/form-data",
      "data": [
        { "name": "AWSAccessKeyId", "value": "AKIAIDPUZISHSBEOFS6Q" },
        { "name": "key", "value": "items/462F1F080M0Q1l0z1p1Y/${filename}" },
        { "name": "policy", "value": "eyJleHBpcmF0aW9uIjoiMjAxMy0wMy0yMFQwMjowNjozM1oiLCJjb25kaXRpb25zIjpbeyJidWNrZXQiOiJkZXYuZi5jbC5seSJ9LFsic3RhcnRzLXdpdGgiLCIka2V5IiwiaXRlbXMvNDYyRjFGMDgwTTBRMWwwejFwMVkvIl0seyJhY2wiOiJwdWJsaWMtcmVhZCJ9LHsic3VjY2Vzc19hY3Rpb25fcmVkaXJlY3QiOiJodHRwOi8vYXBpLmdldGNsb3VkYXBwLmRldi9kcm9wcy81MTMvczM/dG9rZW49YWJjMTIzIn0sWyJjb250ZW50LWxlbmd0aC1yYW5nZSIsMCwyNjIxNDQwMDBdXX0=" },
        { "name": "signature", "value": "KMwdQmgHaqmNQ3+dLTg8oYNytZI=" },
        { "name": "acl", "value": "public-read" },
        { "name": "success_action_redirect", "value": "http://api.getcloudapp.dev/drops/513/s3?token=abc123" },
        { "name": "file", "value": null }
      ]
    },
    "items": [
      {
        "href": "http://api.getcloudapp.dev/drops/513",
        "links": [
          { "rel": "collection", "href": "http://api.getcloudapp.dev/drops" },
          { "rel": "canonical", "href": "http://cl.dev/0o3B0U2z0321" },
          { "rel": "icon", "href": "https://secure.assets.my.cl.dev/images/thumbnails/unknown.png" }
        ],
        "data": [
          { "name": "id", "value": 513 },
          { "name": "name", "value": null },
          { "name": "private", "value": true },
          { "name": "trash", "value": false },
          { "name": "views", "value": 0 },
          { "name": "created", "value": "2013-03-20T01:06:33Z" }
        ]
      }
    ],
    "version": "1.0"
  }
}
```
