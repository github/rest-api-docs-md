# Get all organization roles for an organization

`GET /orgs/{org}/organization-roles`

[API method documentation](https://docs.github.com/rest/orgs/organization-roles#get-all-organization-roles-for-an-organization)

## All Parameters for "Get all organization roles for an organization"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.

## Operation Description

Lists the organization roles available in this organization. For more information on organization roles, see "[Managing people's access to your organization with roles](https://docs.github.com/organizations/managing-peoples-access-to-your-organization-with-roles/about-custom-organization-roles)."

To use this endpoint, the authenticated user must be one of:

- An administrator for the organization.
- A user, or a user on a team, with the fine-grained permissions of `read_organization_custom_org_role` in the organization.

OAuth app tokens and personal access tokens (classic) need the `admin:org` scope to use this endpoint.
