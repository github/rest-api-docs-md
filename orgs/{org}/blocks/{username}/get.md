# Check if a user is blocked by an organization

`GET /orgs/{org}/blocks/{username}`

[API method documentation](https://docs.github.com/rest/orgs/blocking#check-if-a-user-is-blocked-by-an-organization)

## All Parameters for "Check if a user is blocked by an organization"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.
- `username` (string, required): The handle for the GitHub user account.

## Operation Description

Returns a 204 if the given user is blocked by the given organization. Returns a 404 if the organization is not blocking the user, or if the user account has been identified as spam by GitHub.
