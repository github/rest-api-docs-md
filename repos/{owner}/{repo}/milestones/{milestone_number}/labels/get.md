# List labels for issues in a milestone

`GET /repos/{owner}/{repo}/milestones/{milestone_number}/labels`

Lists labels for issues in a milestone.

[API method documentation](https://docs.github.com/rest/issues/labels#list-labels-for-issues-in-a-milestone)

## All Parameters for "List labels for issues in a milestone"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `milestone_number` (integer, required): The number that identifies the milestone.
### Query Parameters

- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."