# Adding an API specification

## Entity relationship diagram

``` mermaid
erDiagram
  API-SPECIFICATION ||--o{ VERSION : contains
  VERSION ||--o{ DECLARATION-OF-CONFORMITY : contains
  API-SPECIFICATION }o..|| ORGANIZATION : references
```

!!! info

    - Exactly one `API-SPECIFICATION` *contains* zero or more `VERSION`
    - Exactly one `VERSION` *contains* zero or more `DECLARATION-OF-CONFORMITY`
    - Zero or more `API-SPECIFICATION` *references* exactly one `ORGANIZATION`

## Add API specification

=== "Request"

    ```json hl_lines="7"
    POST https://api.zorgapis.nl/v1beta1/api-specifications HTTP/1.1
    Content-Type: application/json

    --8<-- "learn/apis/snippets/add-api-specification_request.json"
    ```

    1.  The name of the API specification, must be **unique** for this organization (see `#!js "organizationId"`).
    2.  The UUID of the [organization](../organizations/adding-an-organization.md#add-organization) that maintains the
        API specification.
    3.  The architectural style of the API specification, and therefore of all associated versions. For example,
        `#!js "REST"` or `#!js "SOAP"`.

=== "Response"

    ```json hl_lines="5 9-12"
    HTTP/1.1 201 Created
    Content-Type: application/json

    --8<-- "learn/apis/snippets/add-api-specification_response.json"
    ```

    1.  The Universally Unique Identifier, or UUID (see [RFC 4122](
        https://datatracker.ietf.org/doc/html/rfc4122){: target="_blank" }), assigned to the API specification by the
        API server.

!!! note

    To learn more, view the [API reference](
    https://oas.zorgapis.nl/#tag/api-specifications/operation/addApiSpecification){: target="_blank" }
    or fork our [Postman Collection](
    https://www.postman.com/zorgapis/zorgapis/collection/6oerml3/zorgapis-api){: target="_blank" }
    and explore our API.

## Add API specification version

=== "Request"

    ```json
    POST https://api.zorgapis.nl/v1beta1/api-specifications/fe30bf05-de07-4556-9b17-1f82d62fe45f/versions HTTP/1.1
    Content-Type: application/json

    --8<-- "learn/apis/snippets/add-api-specification-version_request.json"
    ```

    1.  The name of the API specification version, must be **unique** for this API specification.
    2.  The date and time (formatted as per [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601){: target="_blank" }) at
        which the API specification version was published. In other words, the date and time at which this version was
        first made available by the [organization](../organizations/adding-an-organization.md#add-organization) that
        maintains the API specification.

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

    --8<-- "learn/apis/snippets/add-api-specification-version_response.json"
    ```

    1.  The Universally Unique Identifier, or UUID (see [RFC 4122](
        https://datatracker.ietf.org/doc/html/rfc4122){: target="_blank" }), assigned to the API specification version
        by the API server.
    2.  The Universally Unique Identifier, or UUID (see [RFC 4122](
        https://datatracker.ietf.org/doc/html/rfc4122){: target="_blank" }), assigned to the API specification version
        URL by the API server.

!!! note

    To learn more, view the [API reference](
    https://oas.zorgapis.nl/#tag/api-specifications.versions/operation/addApiSpecificationVersion){: target="_blank" }
    or fork our [Postman Collection](
    https://www.postman.com/zorgapis/zorgapis/collection/6oerml3/zorgapis-api){: target="_blank" }
    and explore our API.

## Add declaration of conformity

This section guides you through the process of validating your API specification against the
[requirements for APIs in Dutch Healthcare](https://www.zorgapis.nl/en/api-requirements?perspectiveTypes=API_SPECIFICATION){: target="_blank" }.
As part of this process, you will perform a self-assessment to determine whether your API specification is conformant.

### The importance of transparency

Transparency is a key aspect of this process. By making the results of your declaration of conformity publicly
available, we ensure an environment of openness and accountability. Suppliers are encouraged to submit accurate results,
knowing that their declarations will be published in the [API Library for Dutch Healthcare](
https://www.zorgapis.nl/){: target="_blank" }. Results will be visible to everyone and can be independently verified
based on the provided evidence.

!!! warning

    You must [provide evidence](#providing-evidence) supporting compliance claims. Detailed documentation helps maintain
    the integrity and credibility of your declaration.

### Declarations are immutable

It is important to note that a declaration of conformity cannot be changed after it has been submitted. Similar to a
`git commit` command, a new and permanent snapshot of the API specification's current rankings and standardization level
is recorded into your history.

!!! info

    Although you cannot alter a submitted declaration, you can always add new declarations to reflect updates or
    changes. The most recently submitted declaration will be used to display your ranking levels in the
    [API Library for Dutch Healthcare](https://www.zorgapis.nl/){: target="_blank" }.

### Providing evidence

To support your compliance with standards, specifications, guidelines, practices, policies, or laws, you must provide
evidence. This may include URLs to official third-party validation reports or audits (see
[SD010](https://nictiz.github.io/api-requirements-docs/v1.2.0/api-specification-and-documentation/#sd010-when-documentation-claims-compliance-to-standards-specifications-guidelines-and-practices-policies-or-law-documentation-must-provide-references-to-evidence-to-back-up-these-claims){: target="_blank" }).

The `remarks` field is available for you to provide evidence for compliance claims or to explain why specific
requirements may not apply to your API specification.

!!! note

    [Markdown](https://www.markdownguide.org/basic-syntax/){: target="_blank" } is supported for the `remarks` field.
    You can use Markdown syntax to format text, include links and more to enhance the readability and organization of
    your remarks.

### Architectural styles

When adding a declaration of conformity, it is crucial te recognize that certain requirements may only apply to specific
architectural styles. Each architectural style, such as
[REST](https://www.zorgapis.nl/en/api-requirements?perspectiveTypes=API_SPECIFICATION&architecturalStyles=REST){: target="_blank" },
SOAP, GraphQL, OData, or gRPC, has its own unique set of requirements. This approach ensures that rankings are
meaningful and consistent, allowing for a fair comparison between APIs that share the same architectural principles. 

!!! info

    You set the architectural style when [adding an API specification](#add-api-specification). This architectural style
    will apply to the API specification and all of its versions.

When you publish a declaration of conformity, you must use the set of requirements specific to the architectural style
you selected when adding the API specification.

!!! note

    If an expected requirement is missing, the ZorgAPIs API server will return an error. If an extra requirement is
    provided that is not part of the expected set, the API server will ignore it.

We provide code snippets in JSON format to assist you in creating a declaration. These examples can be easily copied and
used with our
[Postman Collection](https://www.postman.com/zorgapis/zorgapis/collection/6oerml3/zorgapis-api){: target="_blank" }.

??? example "Expand to show snippets"

    === "REST"

        ```json
        --8<-- "learn/apis/snippets/declaration-of-conformity_1_2_0_rest.json"
        ```

        1.  The name of the API requirements version, for example `#!js "1.2.0"`, against which to validate this version
            of the API specification.

    === "SOAP"

        ```json
        --8<-- "learn/apis/snippets/declaration-of-conformity_1_2_0_soap.json"
        ```

    === "GraphQL"

        ```json
        --8<-- "learn/apis/snippets/declaration-of-conformity_1_2_0_other.json"
        ```

    === "OData"

        ```json
        --8<-- "learn/apis/snippets/declaration-of-conformity_1_2_0_other.json"
        ```

    === "gRPC"

        ```json
        --8<-- "learn/apis/snippets/declaration-of-conformity_1_2_0_other.json"
        ```

    === "Other"

        ```json
        --8<-- "learn/apis/snippets/declaration-of-conformity_1_2_0_other.json"
        ```

### Example

=== "Request"

    ```json
    POST https://api.zorgapis.nl/v1beta1/api-specifications/fe30bf05-de07-4556-9b17-1f82d62fe45f/versions/15261fd0-b292-45d9-b6b1-266cc922fb50/declarations-of-conformity HTTP/1.1
    Content-Type: application/json

    --8<-- "learn/apis/snippets/add-declaration-of-conformity_request.json"
    ```

    1.  The name of the API requirements version, for example `#!js "1.2.0"`, against which to validate this version of
        the API specification.
    2.  Conformity evaluation has passed, the resource is conformant.
    3.  Conformity evaluation has not passed, the resource is not conformant.
    4.  Conformity evaluation is not applicable to the resource.

=== "Response"

    ```json hl_lines="5 7-21"
    HTTP/1.1 201 Created
    Content-Type: application/json

    --8<-- "learn/apis/snippets/add-declaration-of-conformity_response.json"
    ```

!!! note

    To learn more, view the [API reference](
    https://oas.zorgapis.nl/#tag/api-specifications.versions.declarations-of-conformity/operation/addApiSpecificationVersionDeclarationOfConformity){: target="_blank" }
    or fork our [Postman Collection](
    https://www.postman.com/zorgapis/zorgapis/collection/6oerml3/zorgapis-api){: target="_blank" }
    and explore our API.

## Set API specification main version

=== "Request"

    ```json hl_lines="5"
    PATCH https://api.zorgapis.nl/v1beta1/api-specifications/fe30bf05-de07-4556-9b17-1f82d62fe45f HTTP/1.1
    Content-Type: application/json

    --8<-- "learn/apis/snippets/set-api-specification-main-version_request.json"
    ```

=== "Response"

    ```json hl_lines="15-57"
    HTTP/1.1 20O OK
    Content-Type: application/json

    --8<-- "learn/apis/snippets/set-api-specification-main-version_response.json"
    ```

!!! note

    To learn more, view the [API reference](
    https://oas.zorgapis.nl/#tag/api-specifications/operation/updateApiSpecification){: target="_blank" }
    or fork our [Postman Collection](
    https://www.postman.com/zorgapis/zorgapis/collection/6oerml3/zorgapis-api){: target="_blank" }
    and explore our API.