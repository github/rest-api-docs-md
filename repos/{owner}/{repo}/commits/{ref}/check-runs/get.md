# List check runs for a Git reference

`GET /repos/{owner}/{repo}/commits/{ref}/check-runs`

[API method documentation](https://docs.github.com/rest/checks/runs#list-check-runs-for-a-git-reference)

## All Parameters for "List check runs for a Git reference"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `ref` (string, required): The commit reference. Can be a commit SHA, branch name (`heads/BRANCH_NAME`), or tag name (`tags/TAG_NAME`). For more information, see "[Git References](https://git-scm.com/book/en/v2/Git-Internals-Git-References)" in the Git documentation.
### Query Parameters

- `check_name` (string): Returns check runs with the specified `name`.
- `status` (string): Returns check runs with the specified `status`.
- `filter` (string): Filters check runs by their `completed_at` timestamp. `latest` returns the most recent check runs.
- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `app_id` (integer)

## Operation Description

Lists check runs for a commit ref. The `ref` can be a SHA, branch name, or a tag name.

> [!NOTE]
> The endpoints to manage checks only look for pushes in the repository where the check suite or check run were created. Pushes to a branch in a forked repository are not detected and return an empty `pull_requests` array.

If there are more than 1000 check suites on a single git reference, this endpoint will limit check runs to the 1000 most recent check suites. To iterate over all possible check runs, use the [List check suites for a Git reference](https://docs.github.com/rest/reference/checks#list-check-suites-for-a-git-reference) endpoint and provide the `check_suite_id` parameter to the [List check runs in a check suite](https://docs.github.com/rest/reference/checks#list-check-runs-in-a-check-suite) endpoint.

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint on a private repository.
