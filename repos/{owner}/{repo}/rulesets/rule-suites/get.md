# List repository rule suites

`GET /repos/{owner}/{repo}/rulesets/rule-suites`

[API method documentation](https://docs.github.com/rest/repos/rule-suites#list-repository-rule-suites)

## All Parameters for "List repository rule suites"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
### Query Parameters

- `ref` (string): The name of the ref. Cannot contain wildcard characters. Optionally prefix with `refs/heads/` to limit to branches or `refs/tags/` to limit to tags. Omit the prefix to search across all refs. When specified, only rule evaluations triggered for this ref will be returned.
- `time_period` (string): The time period to filter by.

For example, `day` will filter for rule suites that occurred in the past 24 hours, and `week` will filter for insights that occurred in the past 7 days (168 hours).
- `actor_name` (string): The handle for the GitHub user account to filter on. When specified, only rule evaluations triggered by this actor will be returned.
- `rule_suite_result` (string): The rule results to filter on. When specified, only suites with this result will be returned.
- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."

## Operation Description

Lists suites of rule evaluations at the repository level.
For more information, see "[Managing rulesets for a repository](https://docs.github.com/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/managing-rulesets-for-a-repository#viewing-insights-for-rulesets)."
