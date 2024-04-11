# Authorizing a request

ZorgAPIs API uses OAuth 2.0 to ensure that client requests access data securely. With OAuth 2.0, you first retrieve an
access token for the API, then use that token to authenticate future requests.

!!! note

    When exploring our sandbox API, fork our [Postman Collection](
    https://www.postman.com/zorgapis/workspace/zorgapis/collection/32862395-c22bf5f5-a2ec-40df-86a2-7817de5c7203){: target="_blank" }
    and select **Get New Access Token** in the **Authorization** tab of a request. Postman will automatically populate
    the relevant parts of the request. To learn more, go to [Authenticate with OAuth 2.0 authentication in Postman](
    https://learning.postman.com/docs/sending-requests/authorization/oauth-20){: target="_blank" }.

    [Register](https://auth.sandbox.zorgapis.nl/realms/zorgapis/protocol/openid-connect/registrations?response_type=code&client_id=zorgapis.docs&redirect_uri=https%3A%2F%2Fdeveloper.zorgapis.nl){ .md-button .md-button--primary }
    [Log out](https://auth.sandbox.zorgapis.nl/realms/zorgapis/protocol/openid-connect/logout){ .md-button }

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