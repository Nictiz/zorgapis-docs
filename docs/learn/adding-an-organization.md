# Adding an organization

## Add organization

=== "Request"

    ```json
    POST https://api.zorgapis.nl/v1beta1/organizations HTTP/1.1
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

!!! note

    To learn more, view the [API reference](
    https://oas.zorgapis.nl/#tag/organizations/operation/addOrganization){: target="_blank" }
    or fork our [Postman Collection](
    https://www.postman.com/zorgapis/workspace/zorgapis/collection/32862395-c22bf5f5-a2ec-40df-86a2-7817de5c7203){: target="_blank" }
    and explore our sandbox API.