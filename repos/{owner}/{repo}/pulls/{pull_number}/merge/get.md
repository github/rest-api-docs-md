# Check if a pull request has been merged

`GET /repos/{owner}/{repo}/pulls/{pull_number}/merge`

[API method documentation](https://docs.github.com/rest/pulls/pulls#check-if-a-pull-request-has-been-merged)

## All Parameters for "Check if a pull request has been merged"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `pull_number` (integer, required): The number that identifies the pull request.

## Operation Description

Checks if a pull request has been merged into the base branch. The HTTP status of the response indicates whether or not the pull request has been merged; the response body is empty.
