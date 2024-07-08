# List jobs for a workflow run attempt

`GET /repos/{owner}/{repo}/actions/runs/{run_id}/attempts/{attempt_number}/jobs`

Lists jobs for a specific workflow run attempt. You can use parameters to narrow the list of results. For more information
about using parameters, see [Parameters](https://docs.github.com/rest/guides/getting-started-with-the-rest-api#parameters).

Anyone with read access to the repository can use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint  with a private repository.

[API method documentation](https://docs.github.com/rest/actions/workflow-jobs#list-jobs-for-a-workflow-run-attempt)

## All Parameters for "List jobs for a workflow run attempt"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `run_id` (integer, required): The unique identifier of the workflow run.
- `attempt_number` (integer, required): The attempt number of the workflow run.
### Query Parameters

- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."