# Inviting a user to an organization

## Entity relationship diagram

``` mermaid
erDiagram
  ORGANIZATION ||--o{ INVITATION : contains
  ORGANIZATION ||--|{ MEMBERSHIP : contains
  INVITATION ||..o| USER : references
  MEMBERSHIP ||..|| USER : references
```

!!! info

    - Exactly one `ORGANIZATION` *contains* zero or more `INVITATION`
    - Exactly one `ORGANIZATION` *contains* one or more `MEMBERSHIP`
    - Exactly one `INVITATION` *references* zero or one `USER`
    - Exactly one `MEMBERSHIP` *references* exactly one `USER`

## Add invitation

=== "Request"

    ```json
    POST https://api.zorgapis.nl/v1beta1/organizations/4a7c2c17-6514-46f8-aa05-6a22fb18b4ad/invitations HTTP/1.1
    Content-Type: application/json

    --8<-- "learn/snippets/add-invitation_request.json"
    ```

    1.  The email address of the user. Each organization can have only one pending invitation per email address, and the 
        email address cannot belong to an existing member.

=== "Response"

    ```json hl_lines="5"
    HTTP/1.1 201 Created
    Content-Type: application/json

    --8<-- "learn/snippets/add-invitation_response.json"
    ```

    1.  The Universally Unique Identifier, or UUID (see [RFC 4122](
        https://datatracker.ietf.org/doc/html/rfc4122){: target="_blank" }), assigned to the invitation by the API
        server.
    2.  The status of the invitation. For example, `#!js "PENDING"` or `#!js "ACCEPTED"`.

!!! note

    To learn more, view the [API reference](
    https://oas.zorgapis.nl/#tag/organizations.invitations/operation/addOrganizationInvitation){: target="_blank" }
    or fork our [Postman Collection](
    https://www.postman.com/zorgapis/workspace/zorgapis/collection/32862395-c22bf5f5-a2ec-40df-86a2-7817de5c7203){: target="_blank" }
    and explore our API.