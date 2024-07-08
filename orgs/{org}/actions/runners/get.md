# List self-hosted runners for an organization

`GET /orgs/{org}/actions/runners`

Lists all self-hosted runners configured in an organization.

Authenticated users must have admin access to the organization to use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `admin:org` scope to use this endpoint. If the repository is private, the `repo` scope is also required.

[API method documentation](https://docs.github.com/rest/actions/self-hosted-runners#list-self-hosted-runners-for-an-organization)

## All Parameters for "List self-hosted runners for an organization"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.
### Query Parameters

- `name` (string): The name of a self-hosted runner.
- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."