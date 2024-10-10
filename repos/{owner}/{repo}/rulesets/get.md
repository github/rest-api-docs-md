# Get all repository rulesets

`GET /repos/{owner}/{repo}/rulesets`

[API method documentation](https://docs.github.com/rest/repos/rules#get-all-repository-rulesets)

## All Parameters for "Get all repository rulesets"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
### Query Parameters

- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `includes_parents` (boolean): Include rulesets configured at higher levels that apply to this repository
- `targets` (string): A comma-separated list of rule targets to filter by.
If provided, only rulesets that apply to the specified targets will be returned.
For example, `branch,tag,push`.


## Operation Description

Get all the rulesets for a repository.
