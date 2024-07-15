# Get an environment variable

`GET /repos/{owner}/{repo}/environments/{environment_name}/variables/{name}`

[API method documentation](https://docs.github.com/rest/actions/variables#get-an-environment-variable)

## All Parameters for "Get an environment variable"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `environment_name` (string, required): The name of the environment. The name must be URL encoded. For example, any slashes in the name must be replaced with `%2F`.
- `name` (string, required): The name of the variable.

## Operation Description

Gets a specific variable in an environment.

Authenticated users must have collaborator access to a repository to create, update, or read variables.

OAuth tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.
