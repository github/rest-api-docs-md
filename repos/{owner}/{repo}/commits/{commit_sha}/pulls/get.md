# List pull requests associated with a commit

`GET /repos/{owner}/{repo}/commits/{commit_sha}/pulls`

Lists the merged pull request that introduced the commit to the repository. If the commit is not present in the default branch, will only return open pull requests associated with the commit.

To list the open or merged pull requests associated with a branch, you can set the `commit_sha` parameter to the branch name.

[API method documentation](https://docs.github.com/rest/commits/commits#list-pull-requests-associated-with-a-commit)

## All Parameters for "List pull requests associated with a commit"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `commit_sha` (string, required): The SHA of the commit.
### Query Parameters

- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."