# Download workflow run attempt logs

`GET /repos/{owner}/{repo}/actions/runs/{run_id}/attempts/{attempt_number}/logs`

[API method documentation](https://docs.github.com/rest/actions/workflow-runs#download-workflow-run-attempt-logs)

## All Parameters for "Download workflow run attempt logs"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `run_id` (integer, required): The unique identifier of the workflow run.
- `attempt_number` (integer, required): The attempt number of the workflow run.

## Operation Description

Gets a redirect URL to download an archive of log files for a specific workflow run attempt. This link expires after
1 minute. Look for `Location:` in the response header to find the URL for the download.

Anyone with read access to the repository can use this endpoint.

If the repository is private, OAuth tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.
