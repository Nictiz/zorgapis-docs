# Adding a communication standard

## Entity relationship diagram

``` mermaid
erDiagram
  COMMUNICATION-STANDARD ||--o{ VERSION : contains
  COMMUNICATION-STANDARD }o..|| ORGANIZATION : references
```

!!! info

    - Exactly one `COMMUNICATION-STANDARD` *contains* zero or more `VERSION`
    - Zero or more `COMMUNICATION-STANDARD` *references* exactly one `ORGANIZATION`

## Add communication standard

=== "Request"

    ```json hl_lines="7"
    POST https://api.zorgapis.nl/v1beta1/communication-standards HTTP/1.1
    Content-Type: application/json

    --8<-- "learn/standards/snippets/add-communication-standard_request.json"
    ```

    1.  The name of the communication standard, must be **unique** for this organization (see `#!js "organizationId"`).
    2.  The UUID of the [organization](../organizations/adding-an-organization.md#add-organization) that maintains the
        communication standard.

=== "Response"

    ```json hl_lines="5 9-12"
    HTTP/1.1 201 Created
    Content-Type: application/json

    --8<-- "learn/standards/snippets/add-communication-standard_response.json"
    ```

    1.  The Universally Unique Identifier, or UUID (see [RFC 4122](
        https://datatracker.ietf.org/doc/html/rfc4122){: target="_blank" }), assigned to the commmunication standard by
        the API server.

!!! note

    To learn more, view the [API reference](
    https://oas.zorgapis.nl/#tag/communication-standards/operation/addCommunicationStandard){: target="_blank" }
    or fork our [Postman Collection](
    https://www.postman.com/zorgapis/workspace/zorgapis/collection/32862395-c22bf5f5-a2ec-40df-86a2-7817de5c7203){: target="_blank" }
    and explore our API.

## Add communication standard version

=== "Request"

    ```json hl_lines="7"
    POST https://api.zorgapis.nl/v1beta1/communication-standard-versions HTTP/1.1
    Content-Type: application/json

    --8<-- "learn/standards/snippets/add-communication-standard-version_request.json"
    ```

    1.  The name of the communication standard version, must be **unique** for this communication standard (see
        `#!js "communicationStandardId"`).
    2.  The UUID of the [communication standard](#add-communication-standard) to which this version belongs.
    3.  The date and time (formatted as per [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601){: target="_blank" }) at
        which the communication standard version was published. In other words, the date and time at which this version
        was first made available by the [organization](../organizations/adding-an-organization.md#add-organization) that
        maintains the communication standard.

        **Note**: `publishTime` is **not** to be used for the date and time at which this version is published in the
        API Library for Dutch Healthcare. This value is set automatically by the API server upon creation of the item
        and can be accessed via read-only property `createTime`.
    4.  The [SemVer](https://semver.org/){: target="_blank" } version information. Additional properties for pre-release
        (`#!js "preRelease"`) and build metadata (`#!js "build"`) are available.

=== "Response"

    ```json hl_lines="5 9-12"
    HTTP/1.1 201 Created
    Content-Type: application/json

    --8<-- "learn/standards/snippets/add-communication-standard-version_response.json"
    ```

    1.  The Universally Unique Identifier, or UUID (see [RFC 4122](
        https://datatracker.ietf.org/doc/html/rfc4122){: target="_blank" }), assigned to the communication standard
        version by the API server.

!!! note

    To learn more, view the [API reference](
    https://oas.zorgapis.nl/#tag/communication-standard-versions/operation/addCommunicationStandardVersion){: target="_blank" }
    or fork our [Postman Collection](
    https://www.postman.com/zorgapis/workspace/zorgapis/collection/32862395-c22bf5f5-a2ec-40df-86a2-7817de5c7203){: target="_blank" }
    and explore our API.

## Set communication standard main version