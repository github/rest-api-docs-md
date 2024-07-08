# Get rules for a branch

`GET /repos/{owner}/{repo}/rules/branches/{branch}`

Returns all active rules that apply to the specified branch. The branch does not need to exist; rules that would apply
to a branch with that name will be returned. All active rules that apply will be returned, regardless of the level
at which they are configured (e.g. repository or organization). Rules in rulesets with "evaluate" or "disabled"
enforcement statuses are not returned.

[API method documentation](https://docs.github.com/rest/repos/rules#get-rules-for-a-branch)

## All Parameters for "Get rules for a branch"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `branch` (string, required): The name of the branch. Cannot contain wildcard characters. To use wildcard characters in branch names, use [the GraphQL API](https://docs.github.com/graphql).
### Query Parameters

- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."