# The API is no longer supported

# The CloudApp API



Welcome to the CloudApp developer docs. Here you can find everything you need to
integrate your application with CloudApp. You might want to check out other
great [third-party applications](https://github.com/cloudapp/api/blob/master/third-party-apps.md)
who make use of the API.

There is a good chance most of the work is already cut out for you. A variety of
[third-party client libraries](https://github.com/cloudapp/api/blob/master/wrappers.md)
are available to interface with the CloudApp API.

## Usage

You can use the CloudApp API to [register an account](https://github.com/cloudapp/api/blob/master/register.md),
[list your items](https://github.com/cloudapp/api/blob/master/list-items.md),
[upload a file](https://github.com/cloudapp/api/blob/master/upload-file.md) –
anything [Cloud.app](http://www.getcloudapp.com/) or the [web app](http://my.cl.ly/)
can do. Keep in mind usage of the CloudApp API is bound to our [Terms of
Service](http://getcloudapp.com/terms/).

## Authentication

[HTTP Digest](http://en.wikipedia.org/wiki/Digest_access_authentication) is used
to authenticate all requests.

## JSON

You're probably interested in JSON responses and not HTML. Add the header
`Accept: application/json` on requests to receive JSON and `Content-Type:
application/json` when you're sending JSON.

## Available APIs

### Account

* [Change Default Security](https://github.com/cloudapp/api/blob/master/change-default-security.md)
* [Change Email](https://github.com/cloudapp/api/blob/master/change-email.md)
* [Change Password](https://github.com/cloudapp/api/blob/master/change-password.md)
* [Forgot Password](https://github.com/cloudapp/api/blob/master/forgot-password.md)
* [Register](https://github.com/cloudapp/api/blob/master/register.md)
* [Set Custom Domain](https://github.com/cloudapp/api/blob/master/set-custom-domain.md)
* [View Account Details](https://github.com/cloudapp/api/blob/master/view-account-details.md)
* [View Account Stats](https://github.com/cloudapp/api/blob/master/view-account-stats.md)

### Items

* [Bookmark Link](https://github.com/cloudapp/api/blob/master/bookmark-link.md)
* [Bookmark Multiple Links](https://github.com/cloudapp/api/blob/master/bookmark-multiple-links.md)
* [Change Security of Item](https://github.com/cloudapp/api/blob/master/change-security-of-item.md)
* [Delete Item](https://github.com/cloudapp/api/blob/master/delete-item.md)
* [List Items](https://github.com/cloudapp/api/blob/master/list-items.md)
* [List Items by Source](https://github.com/cloudapp/api/blob/master/list-items-by-source.md)
* [Recover Deleted Item](https://github.com/cloudapp/api/blob/master/recover-deleted-item.md)
* [Rename Item](https://github.com/cloudapp/api/blob/master/rename-item.md)
* [Stream Items](https://github.com/cloudapp/api/blob/master/stream-items.md)
* [Upload File](https://github.com/cloudapp/api/blob/master/upload-file.md)
* [Upload File With Specific Privacy](https://github.com/cloudapp/api/blob/master/upload-file-with-specific-privacy.md)
* [View Domain Details](https://github.com/cloudapp/api/blob/master/view-domain-details.md)
* [View Item](https://github.com/cloudapp/api/blob/master/view-item.md)

### Gift Cards

* [Redeem Gift Card](https://github.com/cloudapp/api/blob/master/redeem-gift-card.md)
* [View Gift Card Details](https://github.com/cloudapp/api/blob/master/view-gift-card-details.md)

## Getting Help

We've done our best to write the CloudApp API documentation to make integrating
with it as simple as possible. Should you have questions we recommend:

* [Ask your question on Stack Overflow](http://stackoverflow.com) and experienced developers can help.
* [Email us if you're completely stuck](mailto:support@getcloudapp.com).

## Help us make it better

Please tell us how we can make the API better. If you have a specific feature
request or if you found a bug, please use GitHub issues. Fork these docs and
send a pull request with improvements.
