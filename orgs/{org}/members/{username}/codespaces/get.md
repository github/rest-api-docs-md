# List codespaces for a user in organization

`GET /orgs/{org}/members/{username}/codespaces`

Lists the codespaces that a member of an organization has for repositories in that organization.

OAuth app tokens and personal access tokens (classic) need the `admin:org` scope to use this endpoint.

[API method documentation](https://docs.github.com/rest/codespaces/organizations#list-codespaces-for-a-user-in-organization)

## All Parameters for "List codespaces for a user in organization"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.
- `username` (string, required): The handle for the GitHub user account.
### Query Parameters

- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."