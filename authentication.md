# Authentication

Authenticate by passing an account's token in the `Authorization` HTTP header.
Exchange account credentials for a token by making an HTTP Basic request to
the authenticate URL. The response will be an [account
representation](representations/account.md).

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
    ...
  }
}
```
