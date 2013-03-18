# View Account Stats

Get the total number of items created and total views for all items of the
authenticated account.

## Request

- Requires [authentication](https://github.com/cloudapp/api/blob/master/README.md#authentication)
- HTTP Method: GET
- URL: http://my.cl.ly/account/stats

## Response

- Status: 200 OK
- Body:

  ```js
  {
    "items": 42,
    "views": 31337
  }
  ```

## Example

```bash
curl --digest -u arthur@dent.com:towel \
     -H "Accept: application/json" \
     "http://my.cl.ly/account/stats"
```