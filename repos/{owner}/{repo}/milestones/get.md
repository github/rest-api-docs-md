# List milestones

`GET /repos/{owner}/{repo}/milestones`

[API method documentation](https://docs.github.com/rest/issues/milestones#list-milestones)

## All Parameters for "List milestones"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
### Query Parameters

- `state` (string): The state of the milestone. Either `open`, `closed`, or `all`.
- `sort` (string): What to sort results by. Either `due_on` or `completeness`.
- `direction` (string): The direction of the sort. Either `asc` or `desc`.
- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."

## Operation Description

Lists milestones for a repository.
