# Get an organization variable

`GET /orgs/{org}/actions/variables/{name}`

[API method documentation](https://docs.github.com/rest/actions/variables#get-an-organization-variable)

## All Parameters for "Get an organization variable"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.
- `name` (string, required): The name of the variable.

## Operation Description

Gets a specific variable in an organization.

The authenticated user must have collaborator access to a repository to create, update, or read variables.

OAuth tokens and personal access tokens (classic) need the`admin:org` scope to use this endpoint. If the repository is private, OAuth tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.
