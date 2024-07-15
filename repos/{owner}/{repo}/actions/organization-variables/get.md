# List repository organization variables

`GET /repos/{owner}/{repo}/actions/organization-variables`

[API method documentation](https://docs.github.com/rest/actions/variables#list-repository-organization-variables)

## All Parameters for "List repository organization variables"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
### Query Parameters

- `per_page` (integer): The number of results per page (max 30). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."

## Operation Description

Lists all organization variables shared with a repository.

Authenticated users must have collaborator access to a repository to create, update, or read variables.

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.
