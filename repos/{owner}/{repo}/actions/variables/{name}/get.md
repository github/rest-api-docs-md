# Get a repository variable

`GET /repos/{owner}/{repo}/actions/variables/{name}`

[API method documentation](https://docs.github.com/rest/actions/variables#get-a-repository-variable)

## All Parameters for "Get a repository variable"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `name` (string, required): The name of the variable.

## Operation Description

Gets a specific variable in a repository.

The authenticated user must have collaborator access to the repository to use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.
