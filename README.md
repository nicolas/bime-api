Making a request
----------------

All URLs start with `https://api.bimeapp.com/v2` excepts for authentication that is scoped by your subdomain `https://youdomain.bimeapp.com/oauth/*`**SSL only**. The path is suffixed with the API version. If we change the API in backward-incompatible ways, we'll bump the version marker and maintain stable support for the old URLs.

You also have to include the `Content-Type` header and the JSON data:

```shell
curl
  -H 'Content-Type: application/json' \
  https://api.bimeapp.com/v2/dashboards
```

That's all!


Authentication
--------------


You must use OAuth 2. This allows users to authorize your application to use Bime on their behalf.

Read the [authentication guide](https://github.com/nicolas/bime-api/blob/master/authentication.md) to get started.


Output format
-------------

We support JSON for serialization of data. Our format is to have no root element and we use snake\_case to describe attribute keys. This means that you have to send `Content-Type: application/json; charset=utf-8` when you're POSTing or PUTing data into Bime.


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
* [Connections](https://github.com/nicolas/bime-api/blob/master/ressources/connections.md)
* [Data security rules](https://github.com/nicolas/bime-api/blob/master/ressources/data_security_rules.md)
* [Named user groups](https://github.com/nicolas/bime-api/blob/master/ressources/named_user_groups.md) 
* [Name user group securities] (https://github.com/nicolas/bime-api/blob/master/ressources/named_user_group_securities.md)
* [Dashboard subscriptions] (https://github.com/nicolas/bime-api/blob/master/ressources/dashboard_subscriptions.md)


How to
----------------
* [integrate a Bime dashboard in a third party solution](https://github.com/nicolas/bime-api/blob/master/usages/dashboard_integration.md) 



Help us make it better
----------------------

Please tell us how we can make the API better. If you have a specific feature request or if you found a bug, please use GitHub issues. 
