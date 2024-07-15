# List secret scanning alerts for a repository

`GET /repos/{owner}/{repo}/secret-scanning/alerts`

[API method documentation](https://docs.github.com/rest/secret-scanning/secret-scanning#list-secret-scanning-alerts-for-a-repository)

## All Parameters for "List secret scanning alerts for a repository"

### Path Parameters

- `owner` (string, required): The account owner of the repository. The name is not case sensitive.
- `repo` (string, required): The name of the repository without the `.git` extension. The name is not case sensitive.
### Query Parameters

- `state` (string): Set to `open` or `resolved` to only list secret scanning alerts in a specific state.
- `secret_type` (string): A comma-separated list of secret types to return. By default all secret types are returned.
See "[Secret scanning patterns](https://docs.github.com/code-security/secret-scanning/secret-scanning-patterns#supported-secrets-for-advanced-security)"
for a complete list of secret types.
- `resolution` (string): A comma-separated list of resolutions. Only secret scanning alerts with one of these resolutions are listed. Valid resolutions are `false_positive`, `wont_fix`, `revoked`, `pattern_edited`, `pattern_deleted` or `used_in_tests`.
- `sort` (string): The property to sort the results by. `created` means when the alert was created. `updated` means when the alert was updated or resolved.
- `direction` (string): The direction to sort the results by.
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `before` (string): A cursor, as given in the [Link header](https://docs.github.com/rest/guides/using-pagination-in-the-rest-api#using-link-headers). If specified, the query only searches for events before this cursor. To receive an initial cursor on your first request, include an empty "before" query string.
- `after` (string): A cursor, as given in the [Link header](https://docs.github.com/rest/guides/using-pagination-in-the-rest-api#using-link-headers). If specified, the query only searches for events after this cursor.  To receive an initial cursor on your first request, include an empty "after" query string.
- `validity` (string): A comma-separated list of validities that, when present, will return alerts that match the validities in this list. Valid options are `active`, `inactive`, and `unknown`.

## Operation Description

Lists secret scanning alerts for an eligible repository, from newest to oldest.

The authenticated user must be an administrator for the repository or for the organization that owns the repository to use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `repo` or `security_events` scope to use this endpoint. If this endpoint is only used with public repositories, the token can use the `public_repo` scope instead.
