# List pending organization invitations

`GET /orgs/{org}/invitations`

The return hash contains a `role` field which refers to the Organization
Invitation role and will be one of the following values: `direct_member`, `admin`,
`billing_manager`, or `hiring_manager`. If the invitee is not a GitHub
member, the `login` field in the return hash will be `null`.

[API method documentation](https://docs.github.com/rest/orgs/members#list-pending-organization-invitations)

## All Parameters for "List pending organization invitations"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.
### Query Parameters

- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `role` (string): Filter invitations by their member role.
- `invitation_source` (string): Filter invitations by their invitation source.