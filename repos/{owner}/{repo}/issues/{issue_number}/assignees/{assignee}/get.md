# Check if a user can be assigned to a issue

`GET /repos/{owner}/{repo}/issues/{issue_number}/assignees/{assignee}`

[API method documentation](https://docs.github.com/rest/issues/assignees#check-if-a-user-can-be-assigned-to-a-issue)

## All Parameters for "Check if a user can be assigned to a issue"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `issue_number` (integer, required): The number that identifies the issue.
- `assignee` (string, required)

## Operation Description

Checks if a user has permission to be assigned to a specific issue.

If the `assignee` can be assigned to this issue, a `204` status code with no content is returned.

Otherwise a `404` status code is returned.
