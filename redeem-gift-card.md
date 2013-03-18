# Redeem Gift Card

Apply a gift card to an account.

## Request

- Requires [authentication](https://github.com/cloudapp/api/blob/master/README.md#authentication)
- HTTP Method: PUT
- URL: https://my.cl.ly/gift_cards/**_gift card code_** _(e.g., https://my.cl.ly/gift\_cards/ABC123)_

## Response

- Status: 200 OK
- Body:

  ```js
  {
    "id":           1,
    "code":         "ABC123",
    "plan":         "pro",
    "months":       12,
    "href":         "https://my.cl.ly/gift_cards/ABC123",
    "created_at":   "2011-01-08T20:11:26Z",
    "updated_at":   "2011-01-08T21:26:26Z",
    "redeemed_at":  "2011-01-08T21:26:26Z",
    "effective_at": "2011-01-10",
    "expires_at":   "2012-01-10"
  }
  ```

## Example

```bash
curl --digest -u arthur@dent.com:towel \
     -H "Accept: application/json" \
     -H "Content-Type: application/json" \
     -X PUT \
     "https://my.cl.ly/gift_cards/ABC123"
```