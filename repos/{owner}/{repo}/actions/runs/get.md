# List workflow runs for a repository

`GET /repos/{owner}/{repo}/actions/runs`

Lists all workflow runs for a repository. You can use parameters to narrow the list of results. For more information about using parameters, see [Parameters](https://docs.github.com/rest/guides/getting-started-with-the-rest-api#parameters).

Anyone with read access to the repository can use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint with a private repository.

This API will return up to 1,000 results for each search when using the following parameters: `actor`, `branch`, `check_suite_id`, `created`, `event`, `head_sha`, `status`.

[API method documentation](https://docs.github.com/rest/actions/workflow-runs#list-workflow-runs-for-a-repository)

## All Parameters for "List workflow runs for a repository"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
### Query Parameters

- `actor` (string): Returns someone's workflow runs. Use the login for the user who created the `push` associated with the check suite or workflow run.
- `branch` (string): Returns workflow runs associated with a branch. Use the name of the branch of the `push`.
- `event` (string): Returns workflow run triggered by the event you specify. For example, `push`, `pull_request` or `issue`. For more information, see "[Events that trigger workflows](https://docs.github.com/actions/automating-your-workflow-with-github-actions/events-that-trigger-workflows)."
- `status` (string): Returns workflow runs with the check run `status` or `conclusion` that you specify. For example, a conclusion can be `success` or a status can be `in_progress`. Only GitHub Actions can set a status of `waiting`, `pending`, or `requested`.
- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `created` (string): Returns workflow runs created within the given date-time range. For more information on the syntax, see "[Understanding the search syntax](https://docs.github.com/search-github/getting-started-with-searching-on-github/understanding-the-search-syntax#query-for-dates)."
- `exclude_pull_requests` (boolean): If `true` pull requests are omitted from the response (empty array).
- `check_suite_id` (integer): Returns workflow runs with the `check_suite_id` that you specify.
- `head_sha` (string): Only returns workflow runs that are associated with the specified `head_sha`.