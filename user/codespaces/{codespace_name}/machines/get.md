# List machine types for a codespace

`GET /user/codespaces/{codespace_name}/machines`

List the machine types a codespace can transition to use.

OAuth app tokens and personal access tokens (classic) need the `codespace` scope to use this endpoint.

[API method documentation](https://docs.github.com/rest/codespaces/machines#list-machine-types-for-a-codespace)

## All Parameters for "List machine types for a codespace"

### Path Parameters

- `codespace_name` (string, required): The name of the codespace.