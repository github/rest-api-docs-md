# Get an organization role

`GET /orgs/{org}/organization-roles/{role_id}`

[API method documentation](https://docs.github.com/rest/orgs/organization-roles#get-an-organization-role)

## All Parameters for "Get an organization role"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.
- `role_id` (integer, required): The unique identifier of the role.

## Operation Description

Gets an organization role that is available to this organization. For more information on organization roles, see "[Using organization roles](https://docs.github.com/organizations/managing-peoples-access-to-your-organization-with-roles/using-organization-roles)."

To use this endpoint, the authenticated user must be one of:

- An administrator for the organization.
- A user, or a user on a team, with the fine-grained permissions of `read_organization_custom_org_role` in the organization.

OAuth app tokens and personal access tokens (classic) need the `admin:org` scope to use this endpoint.
