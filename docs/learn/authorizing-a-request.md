# Authorizing a request

## How the Authorization Code flow works

The example diagram below illustrates the interactions that occur during the [OAuth 2.0 Authorization Code Grant](
https://oauth.net/2/grant-types/authorization-code/){: target="_blank" } flow.

``` mermaid
sequenceDiagram
  participant user as User
  participant client as Application
  participant idp as Authorization server
  participant api as API
  autonumber
  
  activate user
  user->>client: Access
  activate client
  client->>idp: Request authorization
  deactivate client
  activate idp
  idp->>user: Show sign in page
  user->>idp: Sign in with credentials
  deactivate user
  idp->>client: Issue authorization code
  activate client
  client->>idp: Request token
  idp->>idp: Validate request
  idp->>client: Return access token
  deactivate idp
  client->>api: Call API with access token
  activate api
  api->>client: Return data
  deactivate api
  client->>user: Display data
  deactivate client
```

1. A user tries to access the application (the client)
2. The application redirects to the authorization server's `auth` endpoint
    ```html
    https://auth.sandbox.zorgapis.nl/realms/zorgapis/protocol/openid-connect/auth
        ?response_type=code
        &client_id=<client-id> <!-- (1)! -->
        &redirect_uri=<redirect-uri> <!-- (2)! -->
        &scope=<scopes> <!-- (3)! -->
        &state=<state>
    ```

    1.  For example, `zorgapis.postman`.
    2.  For example, `https://oauth.pstmn.io/v1/browser-callback`.
    3.  For example, `api-requirements-versions:read`.

3. The authorization server shows the sign in page
4. The user signs in with its credentials
5. The authorization server issues an authorization code to the application
6. The application requests an access token from the `token` endpoint
    ```html
    POST https://auth.sandbox.zorgapis.nl/realms/zorgapis/protocol/openid-connect/token
        ?grant_type=authorization_code
        &client_id=<client-id>
        &client_secret=<secret>
        &code=<auth-code>
        &redirect_uri=<redirect-uri>
    ```

7. The authorization server validates the request
8. The authorization server returns the access token
9. The application calls a protected API endpoint using the access token
10. The API validates the access token and returns the data
11. The application displays the data to the user