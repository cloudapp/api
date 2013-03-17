---
layout: deprecated
title: Upload File With Specific Privacy
categories: items
---

# Upload File With Specific Privacy

An uploaded file's privacy is set to the
[owner's default privacy setting](/change-default-security). If the file to be
uploaded should be either public or private, this can be overridden when
requesting the parameters to upload a file.

This is simply the first step in the process to upload a file. See the article
[Upload File](/upload-file) for full details.


## Request

- Requires [authentication](https://github.com/cloudapp/api/blob/master/README.md#authentication)
- HTTP Method: GET
- URL: `http://my.cl.ly/items/new?item[private]=false`


## Response

- Status: 200 OK
- Body:

      {
        "uploads_remaining": 10,
        "max_upload_size":   26214400,
        "url":               "http://f.cl.ly",
        "params": {
          "AWSAccessKeyId":          "AKIAIDPUZISHSBEOFS6Q",
          "key":                     "items/qL/${filename}",
          "acl":                     "public-read",
          "success_action_redirect": "http://my.cl.ly/items/s3?item[private]=false",
          "signature":               "2vRWmaSy46WGs0MDUdLHAqjSL8k=",
          "policy":                  "eyJleHBpcmF0aW9uIjoiMjAxMC0wNC0wMVQwMDowMDowMFoiLCJjb25kaXRpb25zIjpbeyJidWNrZXQiOiJsaW5lYnJlYWstdGVzdCJ9LHsiYWNsIjoicHVibGljLXJlYWQifSx7InN1Y2Nlc3NfYWN0aW9uX3JlZGlyZWN0IjoiaHR0cDovL215LmNsb3VkYXBwLmxvY2FsL3VwbG9hZHMvczMifSxbInN0YXJ0cy13aXRoIiwiJGtleSIsInVwbG9hZHMvcUwvIl1dfQ=="
        }
      }


## Errors

If the account is using a CloudApp Free plan, there is a maximum daily file
upload limit. If that limit has been met, the request will be successful but the
`params` attribute will be missing, `uploads_remaining` will be 0, and `message`
will be a friendly explanation of the error.


## Example

{: .shell}
    curl --digest -u arthur@dent.com:towel \
         -H "Accept: application/json" \
         -H "Content-Type: application/json" \
         "http://my.cl.ly/items/new?item[private]=false"
