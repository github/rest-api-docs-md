# List available machine types for a repository

`GET /repos/{owner}/{repo}/codespaces/machines`

[API method documentation](https://docs.github.com/rest/codespaces/machines#list-available-machine-types-for-a-repository)

## All Parameters for "List available machine types for a repository"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
### Query Parameters

- `location` (string): The location to check for available machines. Assigned by IP if not provided.
- `client_ip` (string): IP for location auto-detection when proxying a request
- `ref` (string): The branch or commit to check for prebuild availability and devcontainer restrictions.

## Operation Description

List the machine types available for a given repository based on its configuration.

OAuth app tokens and personal access tokens (classic) need the `codespace` scope to use this endpoint.
