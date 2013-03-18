# Update Drop

Get a drop's details either by [listing drops](/list-drops) or
[viewing a single drop](/view-single-drop).

```bash
$ curl -i -H 'Authorization: Token token="0gc504cf7e4a51ff8119"' \
       "http://api.getcloudapp.com/drops/13949577"

HTTP/1.1 200 OK
Cache-Control: max-age=0, private, must-revalidate
Content-Type: application/vnd.collection+json; charset=utf-8
ETag: "fb83cd304bacd599af0a1e73603500e5"
{
  "collection": {
    "version":  "1.0",
    "href":     "...",
    "template": {
      "data": [
        { "name": "name",         "value": null },
        { "name": "private",      "value": true },
        { "name": "bookmark_url", "value": null },
        { "name": "file_size",    "value": null }
      ]
    },
    "items": [{
      "href":  "...",
      "links": [...],
      "data":  [
        { "name": "id",           "value": 13949577 },
        { "name": "name",         "value": "CloudApp" },
        { "name": "private",      "value": true },
        { "name": "bookmark_url", "value": "http://getcloudapp.com" },
        { "name": "views",        "value": 3 }
      ]
    }]
  }
}
```

Following the Collection+JSON spec, copy the drop's `data` into `template`
ignoring any properties that don't exist in `template`, update any desired
properties, encode the `template` data as `application/json`, and send it as an
HTTP PUT request to the drop's `href`.

**TODO:** This resource MUST accept `application/vnd.collection+json` as per the
Collection+JSON spec.

```bash
$ curl -i -H 'Authorization: Token token="0gc504cf7e4a51ff8119"' \
       -H "Content-Type: application/json; charset=utf-8" \
       -X PUT \
       -d '{
             "name":         "Renamed Drop",
             "private":      true,
             "bookmark_url": null,
             "file_size":    null
           }' \
       "http://api.getcloudapp.com/drops/13949577"

HTTP/1.1 200 OK
Cache-Control: max-age=0, private, must-revalidate
Content-Type: application/vnd.collection+json; charset=utf-8
Etag: "3981883fe2e30e480c700aeee20d6346"
{
  "collection": {
    "version":  "1.0",
    "href":     "...",
    "template": {
      "data": [
        { "name": "name",         "value": null },
        { "name": "private",      "value": true },
        { "name": "bookmark_url", "value": null },
        { "name": "file_size",    "value": null }
      ]
    },
    "items": [{
      "href":  "...",
      "links": [...],
      "data":  [
        { "name": "id",           "value": 13949577 },
        { "name": "name",         "value": "Renamed Drop" },
        { "name": "private",      "value": true },
        { "name": "bookmark_url", "value": "http://getcloudapp.com" },
        { "name": "views",        "value": 3 }
      ]
    }]
  }
}
```