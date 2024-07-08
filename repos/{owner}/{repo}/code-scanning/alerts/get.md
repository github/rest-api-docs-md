# List code scanning alerts for a repository

`GET /repos/{owner}/{repo}/code-scanning/alerts`

Lists code scanning alerts.

The response includes a `most_recent_instance` object.
This provides details of the most recent instance of this alert
for the default branch (or for the specified Git reference if you used `ref` in the request).

OAuth app tokens and personal access tokens (classic) need the `security_events` scope to use this endpoint with private or public repositories, or the `public_repo` scope to use this endpoint with only public repositories.

[API method documentation](https://docs.github.com/rest/code-scanning/code-scanning#list-code-scanning-alerts-for-a-repository)

## All Parameters for "List code scanning alerts for a repository"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
### Query Parameters

- `tool_name`: The name of a code scanning tool. Only results by this tool will be listed. You can specify the tool by using either `tool_name` or `tool_guid`, but not both.
- `tool_guid`: The GUID of a code scanning tool. Only results by this tool will be listed. Note that some code scanning tools may not include a GUID in their analysis data. You can specify the tool by using either `tool_guid` or `tool_name`, but not both.
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `ref`: The Git reference for the results you want to list. The `ref` for a branch can be formatted either as `refs/heads/<branch name>` or simply `<branch name>`. To reference a pull request use `refs/pull/<number>/merge`.
- `direction` (string): The direction to sort the results by.
- `sort` (string): The property by which to sort the results.
- `state`: If specified, only code scanning alerts with this state will be returned.
- `severity`: If specified, only code scanning alerts with this severity will be returned.