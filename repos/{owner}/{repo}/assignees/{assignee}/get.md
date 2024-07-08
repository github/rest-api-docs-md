# Check if a user can be assigned

`GET /repos/{owner}/{repo}/assignees/{assignee}`

Checks if a user has permission to be assigned to an issue in this repository.

If the `assignee` can be assigned to issues in the repository, a `204` header with no content is returned.

Otherwise a `404` status code is returned.

[API method documentation](https://docs.github.com/rest/issues/assignees#check-if-a-user-can-be-assigned)

## All Parameters for "Check if a user can be assigned"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `assignee` (string, required)