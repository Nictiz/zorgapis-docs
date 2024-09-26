# Getting communication standards

## Entity relationship diagram

--8<-- "learn/standards/snippets/communication-standard-entity-relationship-diagram.md"

## Get communication standards

=== "Request"

    ```json
    GET https://api.zorgapis.nl/v1beta1/communication-standards HTTP/1.1
    ```

=== "Response"

    ```json hl_lines="6 15"
    HTTP/1.1 200 OK
    Content-Type: application/json

    --8<-- "learn/standards/snippets/get-communication-standards_response.json"
    ```

    1.  The UUID of the [communication standard](./adding-a-communication-standard.md#add-communication-standard).
    2.  The UUID of the [main version](./adding-a-communication-standard.md#set-communication-standard-main-version-request).

!!! note

    To learn more, view the [API reference](
    https://oas.zorgapis.nl/#tag/communication-standards/operation/listCommunicationStandards){: target="_blank" }
    or fork our [Postman Collection](
    https://www.postman.com/zorgapis/zorgapis/collection/6oerml3/zorgapis-api){: target="_blank" }
    and explore our API.

## Get communication standard versions

List all versions for the communication standard with id `#!js "05d8de10-1932-4e7f-badf-655c1a82fcc3"`:

=== "Request"

    ```json
    GET https://api.zorgapis.nl/v1beta1/communication-standard-versions
        ?filter=eq(communicationStandardId,"05d8de10-1932-4e7f-badf-655c1a82fcc3") HTTP/1.1
    ```

=== "Response"

    ```json hl_lines="6"
    HTTP/1.1 200 OK
    Content-Type: application/json

    --8<-- "learn/standards/snippets/get-communication-standard-versions_response.json"
    ```

!!! note

    To learn more, view the [API reference](
    https://oas.zorgapis.nl/#tag/communication-standard-versions/operation/listCommunicationStandardVersions){: target="_blank" }
    or fork our [Postman Collection](
    https://www.postman.com/zorgapis/zorgapis/collection/6oerml3/zorgapis-api){: target="_blank" }
    and explore our API.