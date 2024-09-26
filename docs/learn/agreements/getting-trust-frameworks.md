# Getting trust frameworks

## Entity relationship diagram

--8<-- "learn/agreements/snippets/trust-framework-entity-relationship-diagram.md"

## Get trust frameworks

=== "Request"

    ```json
    GET https://api.zorgapis.nl/v1beta1/trust-frameworks HTTP/1.1
    ```

=== "Response"

    ```json hl_lines="6 15"
    HTTP/1.1 200 OK
    Content-Type: application/json

    --8<-- "learn/agreements/snippets/get-trust-frameworks_response.json"
    ```

    1.  The UUID of the [trust framework](./adding-a-trust-framework.md#add-trust-framework).
    2.  The UUID of the [main version](./adding-a-trust-framework.md#set-trust-framework-main-version-request).

!!! note

    To learn more, view the [API reference](
    https://oas.zorgapis.nl/#tag/trust-frameworks/operation/listTrustFrameworks){: target="_blank" }
    or fork our [Postman Collection](
    https://www.postman.com/zorgapis/zorgapis/collection/6oerml3/zorgapis-api){: target="_blank" }
    and explore our API.

## Get trust framework versions

List all versions for the trust framework with id `#!js "3b49f2e6-fd5c-48a8-a59c-5fcbed78e5ae"`:

=== "Request"

    ```json
    GET https://api.zorgapis.nl/v1beta1/trust-framework-versions
        ?filter=eq(trustFrameworkId,"3b49f2e6-fd5c-48a8-a59c-5fcbed78e5ae") HTTP/1.1
    ```

=== "Response"

    ```json hl_lines="9"
    HTTP/1.1 200 OK
    Content-Type: application/json

    --8<-- "learn/agreements/snippets/get-trust-framework-versions_response.json"
    ```

!!! note

    To learn more, view the [API reference](
    https://oas.zorgapis.nl/#tag/trust-framework-versions/operation/listTrustFrameworkVersions){: target="_blank" }
    or fork our [Postman Collection](
    https://www.postman.com/zorgapis/zorgapis/collection/6oerml3/zorgapis-api){: target="_blank" }
    and explore our API.