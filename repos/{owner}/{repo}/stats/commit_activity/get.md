# Get the last year of commit activity

`GET /repos/{owner}/{repo}/stats/commit_activity`

[API method documentation](https://docs.github.com/rest/metrics/statistics#get-the-last-year-of-commit-activity)

## All Parameters for "Get the last year of commit activity"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.

## Operation Description

Returns the last year of commit activity grouped by week. The `days` array is a group of commits per day, starting on `Sunday`.
