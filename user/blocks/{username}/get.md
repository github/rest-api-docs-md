# Check if a user is blocked by the authenticated user

`GET /user/blocks/{username}`

[API method documentation](https://docs.github.com/rest/users/blocking#check-if-a-user-is-blocked-by-the-authenticated-user)

## All Parameters for "Check if a user is blocked by the authenticated user"

### Path Parameters

- `username` (string, required): The handle for the GitHub user account.

## Operation Description

Returns a 204 if the given user is blocked by the authenticated user. Returns a 404 if the given user is not blocked by the authenticated user, or if the given user account has been identified as spam by GitHub.
