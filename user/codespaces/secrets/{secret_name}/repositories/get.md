# List selected repositories for a user secret

`GET /user/codespaces/secrets/{secret_name}/repositories`

List the repositories that have been granted the ability to use a user's development environment secret.

The authenticated user must have Codespaces access to use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `codespace` or `codespace:secrets` scope to use this endpoint.

[API method documentation](https://docs.github.com/rest/codespaces/secrets#list-selected-repositories-for-a-user-secret)

## All Parameters for "List selected repositories for a user secret"

### Path Parameters

- `secret_name` (string, required): The name of the secret.