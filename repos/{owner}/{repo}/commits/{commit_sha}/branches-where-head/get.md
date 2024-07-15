# List branches for HEAD commit

`GET /repos/{owner}/{repo}/commits/{commit_sha}/branches-where-head`

[API method documentation](https://docs.github.com/rest/commits/commits#list-branches-for-head-commit)

## All Parameters for "List branches for HEAD commit"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `commit_sha` (string, required): The SHA of the commit.

## Operation Description

Protected branches are available in public repositories with GitHub Free and GitHub Free for organizations, and in public and private repositories with GitHub Pro, GitHub Team, GitHub Enterprise Cloud, and GitHub Enterprise Server. For more information, see [GitHub's products](https://docs.github.com/github/getting-started-with-github/githubs-products) in the GitHub Help documentation.

Returns all branches where the given commit SHA is the HEAD, or latest commit for the branch.
