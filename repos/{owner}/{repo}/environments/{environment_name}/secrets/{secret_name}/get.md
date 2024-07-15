# Get an environment secret

`GET /repos/{owner}/{repo}/environments/{environment_name}/secrets/{secret_name}`

[API method documentation](https://docs.github.com/rest/actions/secrets#get-an-environment-secret)

## All Parameters for "Get an environment secret"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `environment_name` (string, required): The name of the environment. The name must be URL encoded. For example, any slashes in the name must be replaced with `%2F`.
- `secret_name` (string, required): The name of the secret.

## Operation Description

Gets a single environment secret without revealing its encrypted value.

Authenticated users must have collaborator access to a repository to create, update, or read secrets.

OAuth tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.
