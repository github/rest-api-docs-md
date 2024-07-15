# List commit statuses for a reference

`GET /repos/{owner}/{repo}/commits/{ref}/statuses`

[API method documentation](https://docs.github.com/rest/commits/statuses#list-commit-statuses-for-a-reference)

## All Parameters for "List commit statuses for a reference"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `ref` (string, required): The commit reference. Can be a commit SHA, branch name (`heads/BRANCH_NAME`), or tag name (`tags/TAG_NAME`). For more information, see "[Git References](https://git-scm.com/book/en/v2/Git-Internals-Git-References)" in the Git documentation.
### Query Parameters

- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."

## Operation Description

Users with pull access in a repository can view commit statuses for a given ref. The ref can be a SHA, a branch name, or a tag name. Statuses are returned in reverse chronological order. The first status in the list will be the latest one.

This resource is also available via a legacy route: `GET /repos/:owner/:repo/statuses/:ref`.
