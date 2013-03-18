# View Domain Details

Get details about a given domain used by a CloudApp user.

## Request

- HTTP Method: GET
- URL: http://api.cld.me/domains/**domain** _(e.g., http://api.cld.me/domains/dent.com)_

## Response

- Status: 200 OK
- Body:

  ```js
  { "home_page": "http://hhgproject.org" }
  ```

## Example

```bash
curl -H "Accept: application/json" http://api.cld.me/domains/dent.com
```