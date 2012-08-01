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
2. Register your app at [youraccountname.bimeapp.com/oauth_clients](https://youraccountname.bimeapp.com/oauth_clients). You'll be assigned a `client_id` and `client_secret`. You'll need to provide a `redirect_uri`: a URL where we can send a verification code. Just enter a dummy URL like `http://myapp.com/oauth` if you're not ready for this yet.
3. Configure your OAuth 2 library with your `client_id`, `client_secret`, and `redirect_uri`. Tell it to use:

              :request_token_path => "/oauth/request_token"
              :access_token_path  => "/oauth/access_token"
      	 :authorize_path     => "/oauth/authorize"
                    
   and `https://youraccountname.bimeapp.com/` as the base url
   
4. Try making an authorized request to `https://api.bimeapp.com/dashboards` to dig in and test it out!


OAuth 2 from scratch
--------------------

If you're going bare-metal and developing your own OAuth 2 client, you have a bit more work to do.

**TL;DR** request access, receive a verification code, trade it for an access token.

The typical flow for a web app:

1. Your app requests authorization by redirecting your user to Launchpad:
        
        https://youraccountname.bimeapp.com/oauth/authorize?response_type=code&client_id=your-client-id&redirect_uri=your-redirect-uri)

3. We redirect the user back to your app with a time-limited verification code.

4. Your app makes a backchannel request to trade the verification code for an access token. We authenticate your app and issue an access token:

        POST https://youraccountname.bimeapp.com/oauth/access_token?client_id=your-client-id&redirect_uri=your-redirect-uri&client_secret=your-client-secret&code=verification-code

5. Your app uses the token to authorize API requests to any of the Bime ID's accounts. Set the Authorization request header:

        Authorization: Bearer <tokenhere>

Implementation notes:

* Start by reading the [draft spec](http://tools.ietf.org/html/draft-ietf-oauth-v2)
* We implement draft 5 and will update our implementation as the final spec converges. Be prepared for changes along the way.
* We support the web_server and user_agent flows, not the client_credentials or device flows.
* We issue refresh tokens. Use them to request a new access token when it expires (2 week lifetime, currently).
* We return more verbose errors than what's given in the spec to help with client development. We'll move these to a separate parameter later.