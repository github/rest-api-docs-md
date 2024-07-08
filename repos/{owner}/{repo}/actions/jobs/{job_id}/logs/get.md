# Download job logs for a workflow run

`GET /repos/{owner}/{repo}/actions/jobs/{job_id}/logs`

Gets a redirect URL to download a plain text file of logs for a workflow job. This link expires after 1 minute. Look
for `Location:` in the response header to find the URL for the download.

Anyone with read access to the repository can use this endpoint.

If the repository is private, OAuth tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.

[API method documentation](https://docs.github.com/rest/actions/workflow-jobs#download-job-logs-for-a-workflow-run)

## All Parameters for "Download job logs for a workflow run"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `job_id` (integer, required): The unique identifier of the job.