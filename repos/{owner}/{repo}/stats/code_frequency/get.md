# Get the weekly commit activity

`GET /repos/{owner}/{repo}/stats/code_frequency`

[API method documentation](https://docs.github.com/rest/metrics/statistics#get-the-weekly-commit-activity)

## All Parameters for "Get the weekly commit activity"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.

## Operation Description


Returns a weekly aggregate of the number of additions and deletions pushed to a repository.

**Note:** This endpoint can only be used for repositories with fewer than 10,000 commits. If the repository contains
10,000 or more commits, a 422 status code will be returned.

