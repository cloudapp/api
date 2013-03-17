---
layout: deprecated
title: View Domain Details
categories: items
---

# View Domain Details

Get details about a given domain used by a CloudApp user.


## Request

- HTTP Method: GET
- URL: http://api.cld.me/domains/**domain** _(e.g., http://api.cld.me/domains/dent.com)_

## Response

- Status: 200 OK
- Body:

      { "home_page": "http://hhgproject.org" }


## Example

{: .shell}
    curl -H "Accept: application/json" http://api.cld.me/domains/dent.com
