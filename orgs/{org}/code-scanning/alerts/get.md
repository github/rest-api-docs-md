# List code scanning alerts for an organization

`GET /orgs/{org}/code-scanning/alerts`

[API method documentation](https://docs.github.com/rest/code-scanning/code-scanning#list-code-scanning-alerts-for-an-organization)

## All Parameters for "List code scanning alerts for an organization"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.
### Query Parameters

- `tool_name`: The name of a code scanning tool. Only results by this tool will be listed. You can specify the tool by using either `tool_name` or `tool_guid`, but not both.
- `tool_guid`: The GUID of a code scanning tool. Only results by this tool will be listed. Note that some code scanning tools may not include a GUID in their analysis data. You can specify the tool by using either `tool_guid` or `tool_name`, but not both.
- `before` (string): A cursor, as given in the [Link header](https://docs.github.com/rest/guides/using-pagination-in-the-rest-api#using-link-headers). If specified, the query only searches for results before this cursor. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `after` (string): A cursor, as given in the [Link header](https://docs.github.com/rest/guides/using-pagination-in-the-rest-api#using-link-headers). If specified, the query only searches for results after this cursor. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `direction` (string): The direction to sort the results by.
- `state`: If specified, only code scanning alerts with this state will be returned.
- `sort` (string): The property by which to sort the results.
- `severity`: If specified, only code scanning alerts with this severity will be returned.

## Operation Description

Lists code scanning alerts for the default branch for all eligible repositories in an organization. Eligible repositories are repositories that are owned by organizations that you own or for which you are a security manager. For more information, see "[Managing security managers in your organization](https://docs.github.com/organizations/managing-peoples-access-to-your-organization-with-roles/managing-security-managers-in-your-organization)."

The authenticated user must be an owner or security manager for the organization to use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `security_events` or `repo`s cope to use this endpoint with private or public repositories, or the `public_repo` scope to use this endpoint with only public repositories.
