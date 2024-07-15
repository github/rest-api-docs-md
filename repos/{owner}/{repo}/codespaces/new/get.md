# Get default attributes for a codespace

`GET /repos/{owner}/{repo}/codespaces/new`

[API method documentation](https://docs.github.com/rest/codespaces/codespaces#get-default-attributes-for-a-codespace)

## All Parameters for "Get default attributes for a codespace"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
### Query Parameters

- `ref` (string): The branch or commit to check for a default devcontainer path. If not specified, the default branch will be checked.
- `client_ip` (string): An alternative IP for default location auto-detection, such as when proxying a request.

## Operation Description

Gets the default attributes for codespaces created by the user with the repository.

OAuth app tokens and personal access tokens (classic) need the `codespace` scope to use this endpoint.
