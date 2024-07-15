# Get a repository ruleset

`GET /repos/{owner}/{repo}/rulesets/{ruleset_id}`

[API method documentation](https://docs.github.com/rest/repos/rules#get-a-repository-ruleset)

## All Parameters for "Get a repository ruleset"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `ruleset_id` (integer, required): The ID of the ruleset.
### Query Parameters

- `includes_parents` (boolean): Include rulesets configured at higher levels that apply to this repository

## Operation Description

Get a ruleset for a repository.
