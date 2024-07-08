# List organization invitation teams

`GET /orgs/{org}/invitations/{invitation_id}/teams`

List all teams associated with an invitation. In order to see invitations in an organization, the authenticated user must be an organization owner.

[API method documentation](https://docs.github.com/rest/orgs/members#list-organization-invitation-teams)

## All Parameters for "List organization invitation teams"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.
- `invitation_id` (integer, required): The unique identifier of the invitation.
### Query Parameters

- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."