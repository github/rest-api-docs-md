# List repository workflows

`GET /repos/{owner}/{repo}/actions/workflows`

[API method documentation](https://docs.github.com/rest/actions/workflows#list-repository-workflows)

## All Parameters for "List repository workflows"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
### Query Parameters

- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."

## Operation Description

Lists the workflows in a repository.

Anyone with read access to the repository can use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint with a private repository.
