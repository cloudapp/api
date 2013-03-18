# Forgot Password

Dispatch an email containing a link to reset the account's password.

## Request

- HTTP Method: POST
- URL: http://my.cl.ly/reset
- Body:

  ```js
  {
    "user": {
      "email": "arthur@dent.com"
    }
  }
  ```

## Response

- Status: 200 OK

## Example

```bash
curl -H "Accept: application/json" \
     -H "Content-Type: application/json" \
     -d \
       '{
          "user": {
            "email": "arthur@dent.com"
          }
        }' \
     "http://my.cl.ly/reset"
```