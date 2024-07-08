# List check run annotations

`GET /repos/{owner}/{repo}/check-runs/{check_run_id}/annotations`

Lists annotations for a check run using the annotation `id`.

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint on a private repository.

[API method documentation](https://docs.github.com/rest/checks/runs#list-check-run-annotations)

## All Parameters for "List check run annotations"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `check_run_id` (integer, required): The unique identifier of the check run.
### Query Parameters

- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."