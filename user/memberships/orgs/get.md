# List organization memberships for the authenticated user

`GET /user/memberships/orgs`

Lists all of the authenticated user's organization memberships.

[API method documentation](https://docs.github.com/rest/orgs/members#list-organization-memberships-for-the-authenticated-user)

## All Parameters for "List organization memberships for the authenticated user"

### Query Parameters

- `state` (string): Indicates the state of the memberships to return. If not specified, the API returns both active and pending memberships.
- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."