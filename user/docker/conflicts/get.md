# Get list of conflicting packages during Docker migration for authenticated-user

`GET /user/docker/conflicts`

[API method documentation](https://docs.github.com/rest/packages/packages#get-list-of-conflicting-packages-during-docker-migration-for-authenticated-user)


## Operation Description

Lists all packages that are owned by the authenticated user within the user's namespace, and that encountered a conflict during a Docker migration.

OAuth app tokens and personal access tokens (classic) need the `read:packages` scope to use this endpoint.
