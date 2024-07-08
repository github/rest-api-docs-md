# Get a check run

`GET /repos/{owner}/{repo}/check-runs/{check_run_id}`

Gets a single check run using its `id`.

**Note:** The Checks API only looks for pushes in the repository where the check suite or check run were created. Pushes to a branch in a forked repository are not detected and return an empty `pull_requests` array.

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint on a private repository.

[API method documentation](https://docs.github.com/rest/checks/runs#get-a-check-run)

## All Parameters for "Get a check run"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `check_run_id` (integer, required): The unique identifier of the check run.