Bime API Authentication
============================

API requests can be authenticated by passing along an OAuth 2 token.

OAuth 2
-------

For a full app integration, you wouldn't want to get into the business of asking
customers for their passwords -- or storing them! -- so we offer a simple way to
ask a user for access to his account. You get an API access token back without
ever having to see his password or ask him to copy/paste an API key.

1. [Grab an OAuth 2 library](http://oauth.net/code/).
2. Register your app at [integrate.bimeapp.com](https://integrate.bimeapp.com). You'll be assigned a `client_id` and `client_secret`. You'll need to provide a `redirect_uri`: a URL where we can send a verification code. Just enter a dummy URL like `http://myapp.com/oauth` if you're not ready for this yet.
3. Configure your OAuth 2 library with your `client_id`, `client_secret`, and `redirect_uri`. Tell it to use `https://bimeapp.com/authorization/new` to request authorization and `https://bimeapp.com/authorization/token` to get access tokens.
4. Try making an authorized request to `https://bimeapp.com/authorization.json` to dig in and test it out!


OAuth 2 from scratch
--------------------

If you're going bare-metal and developing your own OAuth 2 client, you have a bit more work to do.

**TL;DR** request access, receive a verification code, trade it for an access token.

The typical flow for a web app:

1. Your app requests authorization by redirecting your user to Launchpad:

        https://bimeapp.com/authorization/new?type=web_server&client_id=your-client-id&redirect_uri=your-redirect-uri

2. We authenticate their Bime ID and ask whether it's ok to give access to your app. [Here's an example of what this screen looks like](https://bimeapp.com/authorization/new?type=web_server&client_id=0bf18204f5a28003bf7b9abb7e1db5e649d86ef4&redirect_uri=moist%3A%2F%2Foauth)

3. We redirect the user back to your app with a time-limited verification code.

4. Your app makes a backchannel request to trade the verification code for an access token. We authenticate your app and issue an access token:

        POST https://bimeapp.com/authorization/token?type=web_server&client_id=your-client-id&redirect_uri=your-redirect-uri&client_secret=your-client-secret&code=verification-code

5. Your app uses the token to authorize API requests to any of the Bime ID's accounts. Set the Authorization request header:

        Authorization: Bearer <tokenhere>

6. To get info about the Bime ID you authorized and the accounts you have access to, make an authorized request to `https://bimeapp.com/authorization.json` (or `/authorization.xml`).

Implementation notes:

* Start by reading the [draft spec](http://tools.ietf.org/html/draft-ietf-oauth-v2)
* We implement draft 5 and will update our implementation as the final spec converges. Be prepared for changes along the way.
* We support the web_server and user_agent flows, not the client_credentials or device flows.
* We issue refresh tokens. Use them to request a new access token when it expires (2 week lifetime, currently).
* We return more verbose errors than what's given in the spec to help with client development. We'll move these to a separate parameter later.