---
layout: deprecated
title: Upload File
categories: items
---

# Upload File

Files are uploaded directly to [S3](http://aws.amazon.com/s3/) to be as fast as
possible. The process involves making an initial request to CloudApp retrieving
a few parameters, passing them along with the file itself to S3, following the
redirect response back to CloudApp, and finally receiving the details of the
newly created item.

This process may seem complex at first. Not to worry. There are some great tools
out there like [Charles](http://charlesproxy.com/) to make your life a lot
easier. Don't go it alone!


## Request to Upload

Request to upload a file to CloudApp. If the authenticated account is able to
upload a file, the response will be some metadata that must be passed to S3 in
order to upload a file. Along with the S3 data may be an upload size limitation.
It's encouraged that you compare the size of the file being uploaded to make
sure it's smaller than than the maximum allowed size. Otherwise, the file will
be fully uploaded only to be rejected for being too large.

**Note:** The `uploads_remaining` and `max_upload_size` attributes as well as
`payment` link are optional. For example, a response using an account with a
CloudApp Pro plan will omit both `uploads_remaining` and `payment` because Pro
has unlimited uploads and there are no further upgrade paths.

### Request

- Requires [authentication](https://github.com/cloudapp/api/blob/master/README.md#authentication)
- HTTP Method: GET
- URL: http://my.cl.ly/items/new

### Response With Free Plan

- Status: 200 OK
- Link: `<http://store.getcloudapp.com/cart?email=arthur%40dent.com>; rel="payment"`
- Body:

      {
        "uploads_remaining": 10,
        "max_upload_size":   26214400,
        "url":               "http://f.cl.ly",
        "params": {
          "AWSAccessKeyId":          "AKIAIDPUZISHSBEOFS6Q",
          "key":                     "items/qL/${filename}",
          "acl":                     "public-read",
          "success_action_redirect": "http://my.cl.ly/items/s3",
          "signature":               "2vRWmaSy46WGs0MDUdLHAqjSL8k=",
          "policy":                  "eyJleHBpcmF0aW9uIjoiMjAxMC0wNC0wMVQwMDowMDowMFoiLCJjb25kaXRpb25zIjpbeyJidWNrZXQiOiJsaW5lYnJlYWstdGVzdCJ9LHsiYWNsIjoicHVibGljLXJlYWQifSx7InN1Y2Nlc3NfYWN0aW9uX3JlZGlyZWN0IjoiaHR0cDovL215LmNsb3VkYXBwLmxvY2FsL3VwbG9hZHMvczMifSxbInN0YXJ0cy13aXRoIiwiJGtleSIsInVwbG9hZHMvcUwvIl1dfQ=="
        }
      }

### Response With Pro Plan

- Status: 200 OK
- Body:

      {
        "max_upload_size":   262144000,
        "url":               "http://f.cl.ly",
        "params": {
          "AWSAccessKeyId":          "AKIAIDPUZISHSBEOFS6Q",
          "key":                     "items/qL/${filename}",
          "acl":                     "public-read",
          "success_action_redirect": "http://my.cl.ly/items/s3",
          "signature":               "2vRWmaSy46WGs0MDUdLHAqjSL8k=",
          "policy":                  "eyJleHBpcmF0aW9uIjoiMjAxMC0wNC0wMVQwMDowMDowMFoiLCJjb25kaXRpb25zIjpbeyJidWNrZXQiOiJsaW5lYnJlYWstdGVzdCJ9LHsiYWNsIjoicHVibGljLXJlYWQifSx7InN1Y2Nlc3NfYWN0aW9uX3JlZGlyZWN0IjoiaHR0cDovL215LmNsb3VkYXBwLmxvY2FsL3VwbG9hZHMvczMifSxbInN0YXJ0cy13aXRoIiwiJGtleSIsInVwbG9hZHMvcUwvIl1dfQ=="
        }
      }

### Errors

If the account is using a CloudApp Free plan, there is a maximum daily upload
limit. If that limit has been met, the `params` attribute will be missing, and
`uploads_remaining` will be 0. If there is an upgrade path available, a
`payment` link will be present.

- Status: 200 OK
- Link: `<http://store.getcloudapp.com/cart?email=arthur%40dent.com>; rel="payment"`
- Body:

      {
        "uploads_remaining": 0,
        "max_upload_size":   26214400,
        "url":               "http://f.cl.ly"
      }


## Upload File to S3

Use the response from the previous step to construct the file upload request.
Each item in `params` becomes a separate parameter you'll need to post to `url`.
Send the file to be uploaded as the parameter named `file`.

**Note:** According to [Amazon's documentation][s3-docs], any parameter after
`file` is ignored. Make sure `file` is last or the upload will be rejected.

[s3-docs]: http://developer.amazonwebservices.com/connect/entry.jspa?externalID=1434

### Request

- HTTP Method: POST
- URL: Value of `url` in response. _(e.g., http://f.cl.ly)_
- Post each key and value from `params` as a separate parameter.
- Post the file data as the parameter `file`.

### Response

- Status: 303 See Other


## Follow Redirect

Finally, ping CloudApp and receive the details of the newly uploaded file.

**Note:** Your HTTP library should handle this step transparently for you. In
the unfortunate case that it does not, make the following request to complete
the upload process.

### Request

- Requires [authentication](https://github.com/cloudapp/api/blob/master/README.md#authentication)
- HTTP Method: GET
- URL: Value of `Location` header from previous response. _(e.g., http://my.cl.ly/items/s3)_

### Response

- Status: 200 OK
- Body:

      {
        "href":          "http://my.cl.ly/items/1912559",
        "name":          "CloudApp Logo.png",
        "private":       false,
        "subscribed":    false,
        "url":           "http://cl.ly/2wr4",
        "content_url":   "http://cl.ly/2wr4/CloudApp%20Logo.png",
        "item_type":     "image",
        "view_counter":  0,
        "icon":          "http://my.cl.ly/images/new/item-types/image.png",
        "remote_url":    "http://f.cl.ly/items/7c7aea1395c3db0aee18/CloudApp%20Logo.png",
        "thumbnail_url": "http://thumbs.cl.ly/2wr4",
        "redirect_url":  null,
        "source":        "Cloud/1.5.1 CFNetwork/520.0.13 Darwin/11.0.0 (x86_64) (MacBookPro5%2C5)",
        "created_at":    "2010-10-23T19:50:13Z",
        "updated_at":    "2010-10-23T19:50:13Z",
        "deleted_at":    null
      }
