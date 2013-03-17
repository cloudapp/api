---
layout: deprecated
title: View Gift Card Details
categories: gift_cards
---

# View Gift Card Details

Get the details of an unredeemed gift card.


## Request

- HTTP Method: GET
- URL: https://my.cl.ly/gift_cards/**_gift card code_** _(e.g., https://my.cl.ly/gift\_cards/ABC123)_


## Response

- Status: 200 OK
- Body:

      {
        "id":           1,
        "code":         "ABC123",
        "plan":         "pro",
        "months":       12,
        "href":         "https://my.cl.ly/gift_cards/ABC123",
        "created_at":   "2011-01-08T20:11:26Z",
        "updated_at":   "2011-01-08T20:11:26Z",
        "redeemed_at":  null,
        "effective_at": null,
        "expires_at":   null
      }


## Example

{: .shell}
    curl -H "Accept: application/json" \
         -H "Content-Type: application/json" \
         "https://my.cl.ly/gift_cards/ABC123"
