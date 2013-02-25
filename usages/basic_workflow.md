# Basic Workflow

Code examples are in ruby.

## 1) First setup a client oauth library

< your consumer key > and < your consumer secret > can be find at https://youraccount.bimeapp.com/oauth_clients

    @client ||= OAuth2::Client.new(< your consumer key >,< your consumer secret >,
                                   :site => 'https://youraccount.bimeapp.com/',
                                   :request_token_path => "/oauth/request_token",
                                   :access_token_path  => "/oauth/access_token",
                                   :authorize_path     => "/oauth/authorize",
                                   :parse_json => true
    )


## 2) Authorize your application to access resources of you Bime account

### Get the URL to authorize your app
    auth_url = @client.auth_code.authorize_url(:redirect_uri => "http://yourapplication/redirect_url")

### Redirect browser to the authorization page
    redirect_to auth_url

On a classic workflow, after authorizing the application, you will be redirected to your application with an authorization code (in `params[:code]`)

## Code behind http://yourapplication/redirect_url

    if(params[:code])
      # Exchange the authorization code with an access token (used in future calls to access resources)
      @access_token = @client.auth_code.get_token(params[:code], :redirect_uri => "http://yourapplication/redirect_url")
      # Setup the API endpoint
      @client.site = "https://api.bimeapp.com"
    end

## Make an API call

    resp = @access_token.get "v2/dashboards/" + dahsboard_id
    dashboard = JSON.parse(resp.body)["result"]
