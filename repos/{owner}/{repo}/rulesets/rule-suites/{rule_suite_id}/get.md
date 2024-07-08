# Get a repository rule suite

`GET /repos/{owner}/{repo}/rulesets/rule-suites/{rule_suite_id}`

Gets information about a suite of rule evaluations from within a repository.
For more information, see "[Managing rulesets for a repository](https://docs.github.com/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/managing-rulesets-for-a-repository#viewing-insights-for-rulesets)."

[API method documentation](https://docs.github.com/rest/repos/rule-suites#get-a-repository-rule-suite)

## All Parameters for "Get a repository rule suite"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
- `rule_suite_id` (integer, required): The unique identifier of the rule suite result.
To get this ID, you can use [GET /repos/{owner}/{repo}/rulesets/rule-suites](https://docs.github.com/rest/repos/rule-suites#list-repository-rule-suites)
for repositories and [GET /orgs/{org}/rulesets/rule-suites](https://docs.github.com/rest/orgs/rule-suites#list-organization-rule-suites)
for organizations.