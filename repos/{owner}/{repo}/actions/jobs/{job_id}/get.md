# Get a job for a workflow run

`GET /repos/{owner}/{repo}/actions/jobs/{job_id}`

[API method documentation](https://docs.github.com/rest/actions/workflow-jobs#get-a-job-for-a-workflow-run)

## All Parameters for "Get a job for a workflow run"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `job_id` (integer, required): The unique identifier of the job.

## Operation Description

Gets a specific job in a workflow run.

Anyone with read access to the repository can use this endpoint.

If the repository is private, OAuth tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.
