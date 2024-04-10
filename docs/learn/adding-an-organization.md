# Adding an organization

## Add organization

=== "Request"

    ```json
    POST https://api.sandbox.zorgapis.nl/v1alpha2/organizations HTTP/1.1
    Content-Type: application/json

    --8<-- "learn/snippets/add-organization_request.json"
    ```

    1.  The name of the organization, must be **unique**.

=== "Response"

    ```json hl_lines="5"
    HTTP/1.1 201 Created
    Content-Type: application/json

    --8<-- "learn/snippets/add-organization_response.json"
    ```

    1.  The Universally Unique Identifier, or UUID (see [RFC 4122](
        https://datatracker.ietf.org/doc/html/rfc4122){: target="_blank" }), assigned to the organization by the API
        server.