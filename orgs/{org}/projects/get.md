# List organization projects

`GET /orgs/{org}/projects`

[API method documentation](https://docs.github.com/rest/projects/projects#list-organization-projects)

## All Parameters for "List organization projects"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.
### Query Parameters

- `state` (string): Indicates the state of the projects to return.
- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."

## Operation Description

Lists the projects in an organization. Returns a `404 Not Found` status if projects are disabled in the organization. If you do not have sufficient privileges to perform this action, a `401 Unauthorized` or `410 Gone` status is returned.
