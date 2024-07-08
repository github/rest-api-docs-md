# List app installations for an organization

`GET /orgs/{org}/installations`

Lists all GitHub Apps in an organization. The installation count includes
all GitHub Apps installed on repositories in the organization.

The authenticated user must be an organization owner to use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `admin:read` scope to use this endpoint.

[API method documentation](https://docs.github.com/rest/orgs/orgs#list-app-installations-for-an-organization)

## All Parameters for "List app installations for an organization"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.
### Query Parameters

- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."