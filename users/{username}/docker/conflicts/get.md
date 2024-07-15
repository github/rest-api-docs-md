# Get list of conflicting packages during Docker migration for user

`GET /users/{username}/docker/conflicts`

[API method documentation](https://docs.github.com/rest/packages/packages#get-list-of-conflicting-packages-during-docker-migration-for-user)

## All Parameters for "Get list of conflicting packages during Docker migration for user"

### Path Parameters

- `username` (string, required): The handle for the GitHub user account.

## Operation Description

Lists all packages that are in a specific user's namespace, that the requesting user has access to, and that encountered a conflict during Docker migration.

OAuth app tokens and personal access tokens (classic) need the `read:packages` scope to use this endpoint.
