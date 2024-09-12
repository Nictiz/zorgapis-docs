# Adding an organization

## Add organization

This section guides you through the process of adding your organization to the [API Library for Dutch Healthcare](
https://www.zorgapis.nl/){: target="_blank" } via our API.

!!! info

    You can set the URL of your organization on GitHub or GitLab using the `githubUrl` and `gitlabUrl` properties. This
    URL will be used to retrieve the organization's avatar and display it on the organization page in the API Library
    for Dutch Healthcare.

=== "Request"

    ```json
    POST https://api.zorgapis.nl/v1beta1/organizations HTTP/1.1
    Content-Type: application/json

    --8<-- "learn/organizations/snippets/add-organization_request.json"
    ```

    1.  The name of the organization, must be **unique**.
    2.  The URL of the organization on GitHub. For GitLab, use the `gitlabUrl` property.
    3.  To set the house number addition (for example, 'A'), use the `houseNumberAddition` property.

=== "Response"

    ```json hl_lines="5"
    HTTP/1.1 201 Created
    Content-Type: application/json

    --8<-- "learn/organizations/snippets/add-organization_response.json"
    ```

    1.  The Universally Unique Identifier, or UUID (see [RFC 4122](
        https://datatracker.ietf.org/doc/html/rfc4122){: target="_blank" }), assigned to the organization by the API
        server.

!!! note

    To learn more, view the [API reference](
    https://oas.zorgapis.nl/#tag/organizations/operation/addOrganization){: target="_blank" }
    or fork our [Postman Collection](
    https://www.postman.com/zorgapis/workspace/zorgapis/collection/32862395-c22bf5f5-a2ec-40df-86a2-7817de5c7203){: target="_blank" }
    and explore our API.