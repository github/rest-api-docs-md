# Check if a repository is starred by the authenticated user

`GET /user/starred/{owner}/{repo}`

Whether the authenticated user has starred the repository.

[API method documentation](https://docs.github.com/rest/activity/starring#check-if-a-repository-is-starred-by-the-authenticated-user)

## All Parameters for "Check if a repository is starred by the authenticated user"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.