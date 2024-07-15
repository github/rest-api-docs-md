# Get a check suite

`GET /repos/{owner}/{repo}/check-suites/{check_suite_id}`

[API method documentation](https://docs.github.com/rest/checks/suites#get-a-check-suite)

## All Parameters for "Get a check suite"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `check_suite_id` (integer, required): The unique identifier of the check suite.

## Operation Description

Gets a single check suite using its `id`.

**Note:** The Checks API only looks for pushes in the repository where the check suite or check run were created. Pushes to a branch in a forked repository are not detected and return an empty `pull_requests` array and a `null` value for `head_branch`.

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint on a private repository.
