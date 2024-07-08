# Get an autolink reference of a repository

`GET /repos/{owner}/{repo}/autolinks/{autolink_id}`

This returns a single autolink reference by ID that was configured for the given repository.

Information about autolinks are only available to repository administrators.

[API method documentation](https://docs.github.com/rest/repos/autolinks#get-an-autolink-reference-of-a-repository)

## All Parameters for "Get an autolink reference of a repository"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `autolink_id` (integer, required): The unique identifier of the autolink.