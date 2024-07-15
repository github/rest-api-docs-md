# Get list of conflicting packages during Docker migration for organization

`GET /orgs/{org}/docker/conflicts`

[API method documentation](https://docs.github.com/rest/packages/packages#get-list-of-conflicting-packages-during-docker-migration-for-organization)

## All Parameters for "Get list of conflicting packages during Docker migration for organization"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.

## Operation Description

Lists all packages that are in a specific organization, are readable by the requesting user, and that encountered a conflict during a Docker migration.

OAuth app tokens and personal access tokens (classic) need the `read:packages` scope to use this endpoint.
