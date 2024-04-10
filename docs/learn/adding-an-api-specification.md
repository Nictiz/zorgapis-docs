# Adding an API specification

## Add API specification

=== "Request"

    ```json hl_lines="8"
    POST https://api.sandbox.zorgapis.nl/v1alpha2/api-specifications HTTP/1.1
    Content-Type: application/json

    --8<-- "learn/snippets/add-api-specification_request.json"
    ```

    1.  The name of the API specification, must be **unique** for this organization (see `#!js "organizationId"`).
    2.  The UUID of the [organization](./adding-an-organization.md#add-organization) that maintains the API
        specification.
    3.  The architectural style of the API specification, and therefore of all associated versions. For example,
        `#!js "REST"` or `#!js "SOAP"`.

=== "Response"

    ```json hl_lines="5 10-13"
    HTTP/1.1 201 Created
    Content-Type: application/json

    --8<-- "learn/snippets/add-api-specification_response.json"
    ```

    1.  The Universally Unique Identifier, or UUID (see [RFC 4122](
        https://datatracker.ietf.org/doc/html/rfc4122){: target="_blank" }), assigned to the API specification by the
        API server.

## Add API specification version

=== "Request"

    ```json
    POST https://api.sandbox.zorgapis.nl/v1alpha2/api-specifications/fe30bf05-de07-4556-9b17-1f82d62fe45f/versions HTTP/1.1
    Content-Type: application/json

    --8<-- "learn/snippets/add-api-specification-version_request.json"
    ```

    1.  The name of the API specification version, must be **unique** for this API specification.
    2.  The date and time (formatted as per [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601){: target="_blank" }) at
        which the API specification version was published. In other words, the date and time at which this version was
        first made available by the [organization](./adding-an-organization.md#add-organization) that maintains the API
        specification.

        **Note**: `publishTime` is **not** to be used for the date and time at which this version is published in the
        API Library for Dutch Healthcare. This value is set automatically by the API server upon creation of the item
        and can be accessed via read-only property `createTime`.
    3.  The [SemVer](https://semver.org/){: target="_blank" } version information. Additional properties for pre-release
        (`#!js "preRelease"`) and build metadata (`#!js "build"`) are available.
    4.  The URL type, for example, `#!js "OPENAPI_SPECIFICATION"`.

=== "Response"

    ```json hl_lines="5 17 22"
    HTTP/1.1 201 Created
    Content-Type: application/json

    --8<-- "learn/snippets/add-api-specification-version_response.json"
    ```

    1.  The Universally Unique Identifier, or UUID (see [RFC 4122](
        https://datatracker.ietf.org/doc/html/rfc4122){: target="_blank" }), assigned to the API specification version
        by the API server.
    2.  The Universally Unique Identifier, or UUID (see [RFC 4122](
        https://datatracker.ietf.org/doc/html/rfc4122){: target="_blank" }), assigned to the API specification version
        URL by the API server.

## Add declaration of conformity

=== "Request"

    ```json
    POST https://api.sandbox.zorgapis.nl/v1alpha2/api-specifications/fe30bf05-de07-4556-9b17-1f82d62fe45f/versions/15261fd0-b292-45d9-b6b1-266cc922fb50/declarations-of-conformity HTTP/1.1
    Content-Type: application/json

    --8<-- "learn/snippets/add-declaration-of-conformity_request.json"
    ```

    1.  The name of the API requirements version, for example `#!js "1.2.0"`, against which to validate this version of
        the API specification.

=== "Response"

    ```json hl_lines="5 7-21"
    HTTP/1.1 201 Created
    Content-Type: application/json

    --8<-- "learn/snippets/add-declaration-of-conformity_response.json"
    ```

## Set API specification main version

=== "Request"

    ```json hl_lines="5"
    PATCH https://api.sandbox.zorgapis.nl/v1alpha2/api-specifications/fe30bf05-de07-4556-9b17-1f82d62fe45f HTTP/1.1
    Content-Type: application/json

    --8<-- "learn/snippets/set-api-specification-main-version_request.json"
    ```

=== "Response"

    ```json hl_lines="16-58"
    HTTP/1.1 20O OK
    Content-Type: application/json

    --8<-- "learn/snippets/set-api-specification-main-version_response.json"
    ```