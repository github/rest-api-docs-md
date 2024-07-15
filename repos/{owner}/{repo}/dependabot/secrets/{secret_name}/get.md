# Get a repository secret

`GET /repos/{owner}/{repo}/dependabot/secrets/{secret_name}`

[API method documentation](https://docs.github.com/rest/dependabot/secrets#get-a-repository-secret)

## All Parameters for "Get a repository secret"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `secret_name` (string, required): The name of the secret.

## Operation Description

Gets a single repository secret without revealing its encrypted value.

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.
