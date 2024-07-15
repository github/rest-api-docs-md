# Get an organization membership for the authenticated user

`GET /user/memberships/orgs/{org}`

[API method documentation](https://docs.github.com/rest/orgs/members#get-an-organization-membership-for-the-authenticated-user)

## All Parameters for "Get an organization membership for the authenticated user"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.

## Operation Description

If the authenticated user is an active or pending member of the organization, this endpoint will return the user's membership. If the authenticated user is not affiliated with the organization, a `404` is returned. This endpoint will return a `403` if the request is made by a GitHub App that is blocked by the organization.
