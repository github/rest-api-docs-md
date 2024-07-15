# List Dependabot alerts for a repository

`GET /repos/{owner}/{repo}/dependabot/alerts`

[API method documentation](https://docs.github.com/rest/dependabot/alerts#list-dependabot-alerts-for-a-repository)

## All Parameters for "List Dependabot alerts for a repository"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
### Query Parameters

- `state` (string): A comma-separated list of states. If specified, only alerts with these states will be returned.

Can be: `auto_dismissed`, `dismissed`, `fixed`, `open`
- `severity` (string): A comma-separated list of severities. If specified, only alerts with these severities will be returned.

Can be: `low`, `medium`, `high`, `critical`
- `ecosystem` (string): A comma-separated list of ecosystems. If specified, only alerts for these ecosystems will be returned.

Can be: `composer`, `go`, `maven`, `npm`, `nuget`, `pip`, `pub`, `rubygems`, `rust`
- `package` (string): A comma-separated list of package names. If specified, only alerts for these packages will be returned.
- `manifest` (string): A comma-separated list of full manifest paths. If specified, only alerts for these manifests will be returned.
- `scope` (string): The scope of the vulnerable dependency. If specified, only alerts with this scope will be returned.
- `sort` (string): The property by which to sort the results.
`created` means when the alert was created.
`updated` means when the alert's state last changed.
- `direction` (string): The direction to sort the results by.
- `page` (integer): **Deprecated**. Page number of the results to fetch. Use cursor-based pagination with `before` or `after` instead.
- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `before` (string): A cursor, as given in the [Link header](https://docs.github.com/rest/guides/using-pagination-in-the-rest-api#using-link-headers). If specified, the query only searches for results before this cursor. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `after` (string): A cursor, as given in the [Link header](https://docs.github.com/rest/guides/using-pagination-in-the-rest-api#using-link-headers). If specified, the query only searches for results after this cursor. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `first` (integer): **Deprecated**. The number of results per page (max 100), starting from the first matching result.
This parameter must not be used in combination with `last`.
Instead, use `per_page` in combination with `after` to fetch the first page of results.
- `last` (integer): **Deprecated**. The number of results per page (max 100), starting from the last matching result.
This parameter must not be used in combination with `first`.
Instead, use `per_page` in combination with `before` to fetch the last page of results.

## Operation Description

OAuth app tokens and personal access tokens (classic) need the `security_events` scope to use this endpoint. If this endpoint is only used with public repositories, the token can use the `public_repo` scope instead.
