# Adding a communication standard

## Entity relationship diagram

--8<-- "learn/standards/snippets/communication-standard-entity-relationship-diagram.md"

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
        https://datatracker.ietf.org/doc/html/rfc4122){: target="_blank" }), assigned to the communication standard by
        the API server.

!!! note

    To learn more, view the [API reference](
    https://oas.zorgapis.nl/#tag/communication-standards/operation/addCommunicationStandard){: target="_blank" }
    or fork our [Postman Collection](
    https://www.postman.com/zorgapis/zorgapis/collection/6oerml3/zorgapis-api){: target="_blank" }
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
    https://www.postman.com/zorgapis/zorgapis/collection/6oerml3/zorgapis-api){: target="_blank" }
    and explore our API.

## Set communication standard main version

=== "Request"

    ```json hl_lines="5"
    PATCH https://api.zorgapis.nl/v1beta1/communication-standards/05d8de10-1932-4e7f-badf-655c1a82fcc3 HTTP/1.1
    Content-Type: application/json

    --8<-- "learn/standards/snippets/set-communication-standard-main-version_request.json"
    ```

=== "Response"

    ```json hl_lines="15-27"
    HTTP/1.1 20O OK
    Content-Type: application/json

    --8<-- "learn/standards/snippets/set-communication-standard-main-version_response.json"
    ```

!!! note

    To learn more, view the [API reference](
    https://oas.zorgapis.nl/#tag/communication-standards/operation/updateCommunicationStandard){: target="_blank" }
    or fork our [Postman Collection](
    https://www.postman.com/zorgapis/zorgapis/collection/6oerml3/zorgapis-api){: target="_blank" }
    and explore our API.