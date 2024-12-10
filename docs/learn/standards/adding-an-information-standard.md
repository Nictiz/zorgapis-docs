# Adding an information standard

## Entity relationship diagram

``` mermaid
erDiagram
  INFORMATION-STANDARD ||--o{ VERSION : contains
  INFORMATION-STANDARD }o..|| ORGANIZATION : references
```

!!! info

    - Exactly one `INFORMATION-STANDARD` *contains* zero or more `VERSION`
    - Zero or more `INFORMATION-STANDARD` *references* exactly one `ORGANIZATION`

## Add information standard

=== "Request"

    ```json hl_lines="7"
    POST https://api.zorgapis.nl/v1beta1/information-standards HTTP/1.1
    Content-Type: application/json

    --8<-- "learn/standards/snippets/add-information-standard_request.json"
    ```

    1.  The name of the information standard, must be **unique** for this organization (see `#!js "organizationId"`).
    2.  The UUID of the [organization](../organizations/adding-an-organization.md#add-organization) that maintains the
        information standard.

=== "Response"

    ```json hl_lines="5 9-12"
    HTTP/1.1 201 Created
    Content-Type: application/json

    --8<-- "learn/standards/snippets/add-information-standard_response.json"
    ```

    1.  The Universally Unique Identifier, or UUID (see [RFC 4122](
        https://datatracker.ietf.org/doc/html/rfc4122){: target="_blank" }), assigned to the information standard by
        the API server.

!!! note

    To learn more, view the [API reference](
    https://oas.zorgapis.nl/#tag/information-standards/operation/addInformationStandard){: target="_blank" }
    or fork our [Postman Collection](
    https://www.postman.com/zorgapis/zorgapis/collection/6oerml3/zorgapis-api){: target="_blank" }
    and explore our API.

## Add information standard version

=== "Request"

    ```json hl_lines="7"
    POST https://api.zorgapis.nl/v1beta1/information-standard-versions HTTP/1.1
    Content-Type: application/json

    --8<-- "learn/standards/snippets/add-information-standard-version_request.json"
    ```

    1.  The name of the information standard version, must be **unique** for this information standard (see
        `#!js "informationStandardId"`).
    2.  The UUID of the [information standard](#add-information-standard) to which this version belongs.
    3.  The date and time (formatted as per [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601){: target="_blank" }) at
        which the information standard version was published. In other words, the date and time at which this version
        was first made available by the [organization](../organizations/adding-an-organization.md#add-organization) that
        maintains the information standard.

        **Note**: `publishTime` is **not** to be used for the date and time at which this version is published in the
        API Library for Dutch Healthcare. This value is set automatically by the API server upon creation of the item
        and can be accessed via read-only property `createTime`.
    4.  The [SemVer](https://semver.org/){: target="_blank" } version information. Additional properties for pre-release
        (`#!js "preRelease"`) and build metadata (`#!js "build"`) are available.

=== "Response"

    ```json hl_lines="5 9-12"
    HTTP/1.1 201 Created
    Content-Type: application/json

    --8<-- "learn/standards/snippets/add-information-standard-version_response.json"
    ```

    1.  The Universally Unique Identifier, or UUID (see [RFC 4122](
        https://datatracker.ietf.org/doc/html/rfc4122){: target="_blank" }), assigned to the information standard
        version by the API server.

!!! note

    To learn more, view the [API reference](
    https://oas.zorgapis.nl/#tag/information-standard-versions/operation/addInformationStandardVersion){: target="_blank" }
    or fork our [Postman Collection](
    https://www.postman.com/zorgapis/zorgapis/collection/6oerml3/zorgapis-api){: target="_blank" }
    and explore our API.

## Set information standard main version

=== "Request"

    ```json hl_lines="5"
    PATCH https://api.zorgapis.nl/v1beta1/information-standards/7bc962b1-601d-4759-9a87-68953e7b75e2 HTTP/1.1
    Content-Type: application/json

    --8<-- "learn/standards/snippets/set-information-standard-main-version_request.json"
    ```

=== "Response"

    ```json hl_lines="15-30"
    HTTP/1.1 20O OK
    Content-Type: application/json

    --8<-- "learn/standards/snippets/set-information-standard-main-version_response.json"
    ```

!!! note

    To learn more, view the [API reference](
    https://oas.zorgapis.nl/#tag/information-standards/operation/updateInformationStandard){: target="_blank" }
    or fork our [Postman Collection](
    https://www.postman.com/zorgapis/zorgapis/collection/6oerml3/zorgapis-api){: target="_blank" }
    and explore our API.

## Get information standards

=== "Request"

    ```json
    GET https://api.zorgapis.nl/v1beta1/information-standards HTTP/1.1
    ```

=== "Response"

    ```json hl_lines="6 15"
    HTTP/1.1 200 OK
    Content-Type: application/json

    --8<-- "learn/standards/snippets/get-information-standards_response.json"
    ```

    1.  The UUID of the [information standard](#add-information-standard).
    2.  The UUID of the [main version](#set-information-standard-main-version-request).

!!! note

    To learn more, view the [API reference](
    https://oas.zorgapis.nl/#tag/information-standards/operation/listInformationStandards){: target="_blank" }
    or fork our [Postman Collection](
    https://www.postman.com/zorgapis/zorgapis/collection/6oerml3/zorgapis-api){: target="_blank" }
    and explore our API.

## Get information standard versions

List all versions for the information standard with id `#!js "7bc962b1-601d-4759-9a87-68953e7b75e2"`:

=== "Request"

    ```json
    GET https://api.zorgapis.nl/v1beta1/information-standard-versions
        ?filter=eq(informationStandardId,"7bc962b1-601d-4759-9a87-68953e7b75e2") HTTP/1.1
    ```

=== "Response"

    ```json hl_lines="9"
    HTTP/1.1 200 OK
    Content-Type: application/json

    --8<-- "learn/standards/snippets/get-information-standard-versions_response.json"
    ```

!!! note

    To learn more, view the [API reference](
    https://oas.zorgapis.nl/#tag/information-standard-versions/operation/listInformationStandardVersions){: target="_blank" }
    or fork our [Postman Collection](
    https://www.postman.com/zorgapis/zorgapis/collection/6oerml3/zorgapis-api){: target="_blank" }
    and explore our API.