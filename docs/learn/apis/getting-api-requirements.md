# Getting API requirements

## Entity relationship diagram

``` mermaid
erDiagram
  API-REQUIREMENTS-VERSION ||--o{ API-REQUIREMENT : contains
```

!!! info

    - Exactly one `API-REQUIREMENTS-VERSION` *contains* zero or more `API-REQUIREMENT`

## Get API requirements

List all must-have requirements for API specifications with the REST architectural style:

=== "Request"

    ```json
    GET https://api.zorgapis.nl/v1beta2/api-requirements-versions/1.2.0/api-requirements
        ?filter=and(
            eq(requirementLevel,"MUST"), // (1)!
            any(perspectiveTypes,eq($it,"API_SPECIFICATION")), // (2)!
            any(architecturalStyles,eq($it,"REST")), // (3)!
        ) HTTP/1.1
    ```

    1.  The requirement level must be equal to `#!js "MUST"`.
    2.  The perspective types must include `#!js "API_SPECIFICATION"`.
    3.  The architectural styles must include `#!js "REST"`.

=== "Response"

    ```json hl_lines="6"
    HTTP/1.1 200 OK
    Content-Type: application/json

    --8<-- "learn/apis/snippets/get-api-requirements_response.json"
    ```

    1.  The Universally Unique Identifier, or UUID (see [RFC 4122](
        https://datatracker.ietf.org/doc/html/rfc4122){: target="_blank" }), assigned to the API requirement by the API
        server.
    2.  The roles that apply to the API requirement.
    3.  The perspective types that apply to the API requirement.
    4.  The architectural styles that apply to the API requirement.
    5.  The standardization levels that apply to the API requirement.

!!! note

    To learn more, view the [API reference](
    https://oas.zorgapis.nl/#tag/api-requirements-versions.api-requirements/operation/listApiRequirementsVersionApiRequirements){: target="_blank" }
    or fork our [Postman Collection](
    https://www.postman.com/zorgapis/zorgapis/collection/6oerml3/zorgapis-api){: target="_blank" }
    and explore our API.