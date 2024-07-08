# Get a workflow run attempt

`GET /repos/{owner}/{repo}/actions/runs/{run_id}/attempts/{attempt_number}`

Gets a specific workflow run attempt.

Anyone with read access to the repository can use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint with a private repository.

[API method documentation](https://docs.github.com/rest/actions/workflow-runs#get-a-workflow-run-attempt)

## All Parameters for "Get a workflow run attempt"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `run_id` (integer, required): The unique identifier of the workflow run.
- `attempt_number` (integer, required): The attempt number of the workflow run.
### Query Parameters

- `exclude_pull_requests` (boolean): If `true` pull requests are omitted from the response (empty array).