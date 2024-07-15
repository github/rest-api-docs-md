# List selected repositories for an organization variable

`GET /orgs/{org}/actions/variables/{name}/repositories`

[API method documentation](https://docs.github.com/rest/actions/variables#list-selected-repositories-for-an-organization-variable)

## All Parameters for "List selected repositories for an organization variable"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.
- `name` (string, required): The name of the variable.
### Query Parameters

- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."

## Operation Description

Lists all repositories that can access an organization variable
that is available to selected repositories.

Authenticated users must have collaborator access to a repository to create, update, or read variables.

OAuth app tokens and personal access tokens (classic) need the `admin:org` scope to use this endpoint. If the repository is private, the `repo` scope is also required.
