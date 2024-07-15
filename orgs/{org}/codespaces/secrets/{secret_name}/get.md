# Get an organization secret

`GET /orgs/{org}/codespaces/secrets/{secret_name}`

[API method documentation](https://docs.github.com/rest/codespaces/organization-secrets#get-an-organization-secret)

## All Parameters for "Get an organization secret"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.
- `secret_name` (string, required): The name of the secret.

## Operation Description

Gets an organization development environment secret without revealing its encrypted value.

OAuth app tokens and personal access tokens (classic) need the `admin:org` scope to use this endpoint.
