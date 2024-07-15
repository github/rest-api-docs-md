# Get an organization public key

`GET /orgs/{org}/codespaces/secrets/public-key`

[API method documentation](https://docs.github.com/rest/codespaces/organization-secrets#get-an-organization-public-key)

## All Parameters for "Get an organization public key"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.

## Operation Description

Gets a public key for an organization, which is required in order to encrypt secrets. You need to encrypt the value of a secret before you can create or update secrets.
OAuth app tokens and personal access tokens (classic) need the `admin:org` scope to use this endpoint.
