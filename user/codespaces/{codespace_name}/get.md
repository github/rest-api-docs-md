# Get a codespace for the authenticated user

`GET /user/codespaces/{codespace_name}`

[API method documentation](https://docs.github.com/rest/codespaces/codespaces#get-a-codespace-for-the-authenticated-user)

## All Parameters for "Get a codespace for the authenticated user"

### Path Parameters

- `codespace_name` (string, required): The name of the codespace.

## Operation Description

Gets information about a user's codespace.

OAuth app tokens and personal access tokens (classic) need the `codespace` scope to use this endpoint.
