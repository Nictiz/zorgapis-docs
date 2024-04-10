# Accepting an invitation to join an organization

## Get pending invitations

View the [API reference](https://oas.zorgapis.nl/#tag/users.invitations/operation/listUserInvitations){: target="_blank" }
or [try in Postman](https://www.postman.com/zorgapis/workspace/zorgapis/collection/32862395-c22bf5f5-a2ec-40df-86a2-7817de5c7203){: target="_blank" }.

=== "Request"

    ```json
    GET https://api.sandbox.zorgapis.nl/v1alpha2/users/me/invitations?filter=eq(status,"PENDING") HTTP/1.1
    ```

=== "Response"

    ```json hl_lines="6"
    HTTP/1.1 200 Success
    Content-Type: application/json

    --8<-- "learn/snippets/get-pending-invitations_response.json"
    ```

## Accept pending invitation

View the [API reference](https://oas.zorgapis.nl/#tag/users.invitations/operation/acceptUserInvitation){: target="_blank" }
or [try in Postman](https://www.postman.com/zorgapis/workspace/zorgapis/collection/32862395-c22bf5f5-a2ec-40df-86a2-7817de5c7203){: target="_blank" }.

=== "Request"

    ```json
    POST https://api.sandbox.zorgapis.nl/v1alpha2/users/me/invitations/88411780-1d25-4bc3-86a5-f2f901d9a900:accept HTTP/1.1
    ```

=== "Response"

    ```json hl_lines="12-13"
    HTTP/1.1 200 Success
    Content-Type: application/json

    --8<-- "learn/snippets/accept-pending-invitation_response.json"
    ```

    1.  The date and time (formatted as per [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601){: target="_blank" }) at
        which the user responded to the invitation.