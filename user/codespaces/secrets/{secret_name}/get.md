# Get a secret for the authenticated user

`GET /user/codespaces/secrets/{secret_name}`

[API method documentation](https://docs.github.com/rest/codespaces/secrets#get-a-secret-for-the-authenticated-user)

## All Parameters for "Get a secret for the authenticated user"

### Path Parameters

- `secret_name` (string, required): The name of the secret.

## Operation Description

Gets a development environment secret available to a user's codespaces without revealing its encrypted value.

The authenticated user must have Codespaces access to use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `codespace` or `codespace:secrets` scope to use this endpoint.
