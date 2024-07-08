# Get an organization secret

`GET /orgs/{org}/actions/secrets/{secret_name}`

Gets a single organization secret without revealing its encrypted value.

The authenticated user must have collaborator access to a repository to create, update, or read secrets

OAuth tokens and personal access tokens (classic) need the`admin:org` scope to use this endpoint. If the repository is private, OAuth tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.

[API method documentation](https://docs.github.com/rest/actions/secrets#get-an-organization-secret)

## All Parameters for "Get an organization secret"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.
- `secret_name` (string, required): The name of the secret.