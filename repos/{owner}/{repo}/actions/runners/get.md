# List self-hosted runners for a repository

`GET /repos/{owner}/{repo}/actions/runners`

[API method documentation](https://docs.github.com/rest/actions/self-hosted-runners#list-self-hosted-runners-for-a-repository)

## All Parameters for "List self-hosted runners for a repository"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
### Query Parameters

- `name` (string): The name of a self-hosted runner.
- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."

## Operation Description

Lists all self-hosted runners configured in a repository.

Authenticated users must have admin access to the repository to use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.
