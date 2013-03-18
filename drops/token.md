# Retrieve Account Token

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

Fill `template` with the account email and password, encode each name and value
pair in `data` as `application/json`, and `POST` it to the collection's `href`.

**TODO:** This resource MUST accept `application/vnd.collection+json` as per the
Collection+JSON spec.

```bash
$ curl -i -H "Content-Type: application/json; charset=utf-8" \
       -X POST \
       -d '{
             "email"    : "arthur@dent.com",
             "password" : "towel"
           }' \
       "http://api.getcloudapp.com/account/token"

HTTP/1.1 201 Created
Cache-Control: max-age=0, private, must-revalidate
Content-Type: application/vnd.collection+json; charset=utf-8
Etag: "4438a3f4f703a01c251b7ecc1feab772"
{
  "collection" :
  {
    "version" : "1.0",
    "href"    : "...",
    "links"   :
    [
      { "rel" : "root", "href" : "..." }
    ],
    "items" :
    [
      {
        "href" : "...",
        "data" :
        [
          { "name" : "token", "value" : "0gc504cf7e4a51ff8119" }
        ]
      }
    ]
  }
}
```

Add the value of the token returned to the `Authorization` header in the format
`Token token="<value>"` and follow the `root` link.

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