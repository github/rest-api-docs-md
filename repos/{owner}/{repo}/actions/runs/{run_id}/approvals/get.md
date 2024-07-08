# Get the review history for a workflow run

`GET /repos/{owner}/{repo}/actions/runs/{run_id}/approvals`

Anyone with read access to the repository can use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint with a private repository.

[API method documentation](https://docs.github.com/rest/actions/workflow-runs#get-the-review-history-for-a-workflow-run)

## All Parameters for "Get the review history for a workflow run"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `run_id` (integer, required): The unique identifier of the workflow run.