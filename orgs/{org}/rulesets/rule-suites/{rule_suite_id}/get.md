# Get an organization rule suite

`GET /orgs/{org}/rulesets/rule-suites/{rule_suite_id}`

Gets information about a suite of rule evaluations from within an organization.
For more information, see "[Managing rulesets for repositories in your organization](https://docs.github.com/organizations/managing-organization-settings/managing-rulesets-for-repositories-in-your-organization#viewing-insights-for-rulesets)."

[API method documentation](https://docs.github.com/rest/orgs/rule-suites#get-an-organization-rule-suite)

## All Parameters for "Get an organization rule suite"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.
- `rule_suite_id` (integer, required): The unique identifier of the rule suite result.
To get this ID, you can use [GET /repos/{owner}/{repo}/rulesets/rule-suites](https://docs.github.com/rest/repos/rule-suites#list-repository-rule-suites)
for repositories and [GET /orgs/{org}/rulesets/rule-suites](https://docs.github.com/rest/orgs/rule-suites#list-organization-rule-suites)
for organizations.