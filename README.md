Making a request
----------------

All URLs start with `https://bimeapp.com/api/v1/999999`. **SSL only**. The path is suffixed with the account id and the API version. If we change the API in backward-incompatible ways, we'll bump the version marker and maintain stable support for the old URLs.

To make a request for all the users on your account, you'd append the users index path to the base url to form something like https://bimeapp.com/api/v1/999999/api/v1/users.json. In curl, that looks like:

```shell
curl -u user:pass -H 'User-Agent: MyApp (yourname@example.com)' https://bimeapp.com/api/v1/999999/users.json
```

To create something, it's the same deal except you also have to include the `Content-Type` header and the JSON data:

```shell
curl -u username:password \
  -H 'Content-Type: application/json' \
  -H 'User-Agent: MyApp (yourname@example.com)' \
  -d '{ "name": "My new project!" }' \
  https://bimeapp.com/api/v1/999999/users.json
```

That's all!


Authentication
--------------


You must use OAuth 2. This allows users to authorize your application to use Bime on their behalf.

Read the [authentication guide](https://github.com/nicolas/bime-api/blob/master/authentication.md) to get started.


Identify your app
-----------------

You must include a `User-Agent` header with the name of your application and a link to it or your email address so we can get in touch in case you're doing something wrong (so we may warn you before you're blacklisted) or something awesome (so we may congratulate you). Here's an example:

    User-Agent: Freshbooks (http://freshbooks.com)

If you don't supply this header, you will get a `400 Bad Request`.


Output format
-------------

We support JSON for serialization of data. Our format is to have no root element and we use snake\_case to describe attribute keys. This means that you have to send `Content-Type: application/json; charset=utf-8` when you're POSTing or PUTing data into Bime. **All API URLs end in .json to indicate that they accept and return JSON.**

You'll receive a `415 Unsupported Media Type` response code if you attempt to use a different URL suffix or leave out the `Content-Type` header.



Use HTTP caching
----------------

You must make use of the HTTP freshness headers to lessen the load on our servers (and increase the speed of your application!). Most requests we return will include an `ETag` or `Last-Modified` header. When you first request a resource, store this value, and then submit them back to us on subsequent requests as `If-None-Match` and `If-Modified-Since`. If the resource hasn't changed, you'll see a `304 Not Modified` response, which saves you the time and bandwidth of sending something you already have.


Handling errors
---------------

If Bime is having trouble, you might see a 5xx error. `500` means that the app is entirely down, but you might also see `502 Bad Gateway`, `503 Service Unavailable`, or `504 Gateway Timeout`. It's your responsibility in all of these cases to retry your request later. 



Rate limiting
-------------

You can perform up to 500 requests per 10 second period from the same IP address for the same account. If you exceed this limit, you'll get a [429 Too Many Requests](http://tools.ietf.org/html/draft-nottingham-http-new-status-02#section-4) response for subsequent requests. Check the `Retry-After` header to see how many seconds to wait before retrying the request.



API
-----------------
* [Named users](https://github.com/nicolas/bime-api/blob/master/ressources/named_users.md)
* [Dashboards](https://github.com/nicolas/bime-api/blob/master/ressources/dashboards.md)
* [Models](https://github.com/nicolas/bime-api/blob/master/ressources/dashboards.md)
* [Data security rules](https://github.com/nicolas/bime-api/blob/master/ressources/data_security_rules.md)
* [Named user groups](https://github.com/nicolas/bime-api/blob/master/ressources/named_user_groups.md) 


How to per usage
----------------
* [Integration of Bime dashboard in third party solutions](https://github.com/nicolas/bime-api/bcx-api/blob/master/dashboard_integration.md) 



Help us make it better
----------------------

Please tell us how we can make the API better. If you have a specific feature request or if you found a bug, please use GitHub issues. 
