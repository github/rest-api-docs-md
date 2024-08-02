# List check runs in a check suite

`GET /repos/{owner}/{repo}/check-suites/{check_suite_id}/check-runs`

[API method documentation](https://docs.github.com/rest/checks/runs#list-check-runs-in-a-check-suite)

## All Parameters for "List check runs in a check suite"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `check_suite_id` (integer, required): The unique identifier of the check suite.
### Query Parameters

- `check_name` (string): Returns check runs with the specified `name`.
- `status` (string): Returns check runs with the specified `status`.
- `filter` (string): Filters check runs by their `completed_at` timestamp. `latest` returns the most recent check runs.
- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."

## Operation Description

Lists check runs for a check suite using its `id`.

> [!NOTE]
> The endpoints to manage checks only look for pushes in the repository where the check suite or check run were created. Pushes to a branch in a forked repository are not detected and return an empty `pull_requests` array.

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint on a private repository.
