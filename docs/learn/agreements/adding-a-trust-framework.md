# Adding a trust framework

## Entity relationship diagram

``` mermaid
erDiagram
  TRUST-FRAMEWORK ||--o{ VERSION : contains
  TRUST-FRAMEWORK }o..|| ORGANIZATION : references
```

!!! info

    - Exactly one `TRUST-FRAMEWORK` *contains* zero or more `VERSION`
    - Zero or more `TRUST-FRAMEWORK` *references* exactly one `ORGANIZATION`

## Add trust framework

=== "Request"

    ```json hl_lines="7"
    POST https://api.zorgapis.nl/v1beta1/trust-frameworks HTTP/1.1
    Content-Type: application/json

    --8<-- "learn/agreements/snippets/add-trust-framework_request.json"
    ```

    1.  The name of the trust framework, must be **unique** for this organization (see `#!js "organizationId"`).
    2.  The UUID of the [organization](../organizations/adding-an-organization.md#add-organization) that maintains the
        trust framework.

=== "Response"

    ```json hl_lines="5 9-12"
    HTTP/1.1 201 Created
    Content-Type: application/json

    --8<-- "learn/agreements/snippets/add-trust-framework_response.json"
    ```

    1.  The Universally Unique Identifier, or UUID (see [RFC 4122](
        https://datatracker.ietf.org/doc/html/rfc4122){: target="_blank" }), assigned to the trust framework by
        the API server.

!!! note

    To learn more, view the [API reference](
    https://oas.zorgapis.nl/#tag/trust-frameworks/operation/addTrustFramework){: target="_blank" }
    or fork our [Postman Collection](
    https://www.postman.com/zorgapis/zorgapis/collection/6oerml3/zorgapis-api){: target="_blank" }
    and explore our API.

## Add trust framework version

=== "Request"

    ```json hl_lines="7"
    POST https://api.zorgapis.nl/v1beta1/trust-framework-versions HTTP/1.1
    Content-Type: application/json

    --8<-- "learn/agreements/snippets/add-trust-framework-version_request.json"
    ```

    1.  The name of the trust framework version, must be **unique** for this trust framework (see
        `#!js "trustFrameworkId"`).
    2.  The UUID of the [trust framework](#add-trust-framework) to which this version belongs.
    3.  The date and time (formatted as per [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601){: target="_blank" }) at
        which the trust framework version was published. In other words, the date and time at which this version
        was first made available by the [organization](../organizations/adding-an-organization.md#add-organization) that
        maintains the trust framework.

        **Note**: `publishTime` is **not** to be used for the date and time at which this version is published in the
        API Library for Dutch Healthcare. This value is set automatically by the API server upon creation of the item
        and can be accessed via read-only property `createTime`.
    4.  The [SemVer](https://semver.org/){: target="_blank" } version information. Additional properties for pre-release
        (`#!js "preRelease"`) and build metadata (`#!js "build"`) are available.

=== "Response"

    ```json hl_lines="5 9-12"
    HTTP/1.1 201 Created
    Content-Type: application/json

    --8<-- "learn/agreements/snippets/add-trust-framework-version_response.json"
    ```

    1.  The Universally Unique Identifier, or UUID (see [RFC 4122](
        https://datatracker.ietf.org/doc/html/rfc4122){: target="_blank" }), assigned to the trust framework
        version by the API server.

!!! note

    To learn more, view the [API reference](
    https://oas.zorgapis.nl/#tag/trust-framework-versions/operation/addTrustFrameworkVersion){: target="_blank" }
    or fork our [Postman Collection](
    https://www.postman.com/zorgapis/zorgapis/collection/6oerml3/zorgapis-api){: target="_blank" }
    and explore our API.

## Set trust framework main version

=== "Request"

    ```json hl_lines="5"
    PATCH https://api.zorgapis.nl/v1beta1/trust-frameworks/3d443c34-24a4-4640-bfe5-822627af76e2 HTTP/1.1
    Content-Type: application/json

    --8<-- "learn/agreements/snippets/set-trust-framework-main-version_request.json"
    ```

=== "Response"

    ```json hl_lines="15-27"
    HTTP/1.1 20O OK
    Content-Type: application/json

    --8<-- "learn/agreements/snippets/set-trust-framework-main-version_response.json"
    ```

!!! note

    To learn more, view the [API reference](
    https://oas.zorgapis.nl/#tag/trust-frameworks/operation/updateTrustFramework){: target="_blank" }
    or fork our [Postman Collection](
    https://www.postman.com/zorgapis/zorgapis/collection/6oerml3/zorgapis-api){: target="_blank" }
    and explore our API.

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

    1.  The UUID of the [trust framework](#add-trust-framework).
    2.  The UUID of the [main version](#set-trust-framework-main-version-request).

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