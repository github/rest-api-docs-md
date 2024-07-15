# List workflow run artifacts

`GET /repos/{owner}/{repo}/actions/runs/{run_id}/artifacts`

[API method documentation](https://docs.github.com/rest/actions/artifacts#list-workflow-run-artifacts)

## All Parameters for "List workflow run artifacts"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `run_id` (integer, required): The unique identifier of the workflow run.
### Query Parameters

- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `name` (string): The name field of an artifact. When specified, only artifacts with this name will be returned.

## Operation Description

Lists artifacts for a workflow run.

Anyone with read access to the repository can use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint with a private repository.
