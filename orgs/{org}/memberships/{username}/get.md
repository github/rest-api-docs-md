# Get organization membership for a user

`GET /orgs/{org}/memberships/{username}`

[API method documentation](https://docs.github.com/rest/orgs/members#get-organization-membership-for-a-user)

## All Parameters for "Get organization membership for a user"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.
- `username` (string, required): The handle for the GitHub user account.

## Operation Description

In order to get a user's membership with an organization, the authenticated user must be an organization member. The `state` parameter in the response can be used to identify the user's membership status.
