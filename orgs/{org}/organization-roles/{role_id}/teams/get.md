# List teams that are assigned to an organization role

`GET /orgs/{org}/organization-roles/{role_id}/teams`

Lists the teams that are assigned to an organization role. For more information on organization roles, see "[Managing people's access to your organization with roles](https://docs.github.com/organizations/managing-peoples-access-to-your-organization-with-roles/about-custom-organization-roles)."

To use this endpoint, you must be an administrator for the organization.

OAuth app tokens and personal access tokens (classic) need the `admin:org` scope to use this endpoint.

[API method documentation](https://docs.github.com/rest/orgs/organization-roles#list-teams-that-are-assigned-to-an-organization-role)

## All Parameters for "List teams that are assigned to an organization role"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.
- `role_id` (integer, required): The unique identifier of the role.
### Query Parameters

- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."