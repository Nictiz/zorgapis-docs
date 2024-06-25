# Accepting an invitation to join an organization

## Entity relationship diagram

``` mermaid
erDiagram
  USER ||--o{ INVITATION : contains
  USER ||--o{ MEMBERSHIP : contains
  INVITATION ||..|| ORGANIZATION : references
  MEMBERSHIP ||..|| ORGANIZATION : references
```

!!! info

    - Exactly one `USER` *contains* zero or more `INVITATION`
    - Exactly one `USER` *contains* zero or more `MEMBERSHIP`
    - Exactly one `INVITATION` *references* exactly one `ORGANIZATION`
    - Exactly one `MEMBERSHIP` *references* exactly one `ORGANIZATION`

## Get pending invitations

=== "Request"

    ```json
    GET https://api.zorgapis.nl/v1beta1/users/me/invitations?filter=eq(status,"PENDING") HTTP/1.1
    ```

=== "Response"

    ```json hl_lines="6"
    HTTP/1.1 200 Success
    Content-Type: application/json

    --8<-- "learn/snippets/get-pending-invitations_response.json"
    ```

!!! note

    To learn more, view the [API reference](
    https://oas.zorgapis.nl/#tag/users.invitations/operation/listUserInvitations){: target="_blank" }
    or fork our [Postman Collection](
    https://www.postman.com/zorgapis/workspace/zorgapis/collection/32862395-c22bf5f5-a2ec-40df-86a2-7817de5c7203){: target="_blank" }
    and explore our sandbox API.

## Accept pending invitation

=== "Request"

    ```json
    POST https://api.zorgapis.nl/v1beta1/users/me/invitations/88411780-1d25-4bc3-86a5-f2f901d9a900:accept HTTP/1.1
    ```

=== "Response"

    ```json hl_lines="12-13"
    HTTP/1.1 200 Success
    Content-Type: application/json

    --8<-- "learn/snippets/accept-pending-invitation_response.json"
    ```

    1.  The date and time (formatted as per [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601){: target="_blank" }) at
        which the user responded to the invitation.

!!! note

    To learn more, view the [API reference](
    https://oas.zorgapis.nl/#tag/users.invitations/operation/acceptUserInvitation){: target="_blank" }
    or fork our [Postman Collection](
    https://www.postman.com/zorgapis/workspace/zorgapis/collection/32862395-c22bf5f5-a2ec-40df-86a2-7817de5c7203){: target="_blank" }
    and explore our sandbox API.