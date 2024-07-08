# Get an organization public key

`GET /orgs/{org}/actions/secrets/public-key`

Gets your public key, which you need to encrypt secrets. You need to
encrypt a secret before you can create or update secrets.

The authenticated user must have collaborator access to a repository to create, update, or read secrets.

OAuth tokens and personal access tokens (classic) need the`admin:org` scope to use this endpoint. If the repository is private, OAuth tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.

[API method documentation](https://docs.github.com/rest/actions/secrets#get-an-organization-public-key)

## All Parameters for "Get an organization public key"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.