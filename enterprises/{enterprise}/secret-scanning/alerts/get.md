# List secret scanning alerts for an enterprise

`GET /enterprises/{enterprise}/secret-scanning/alerts`

[API method documentation](https://docs.github.com/rest/secret-scanning/secret-scanning#list-secret-scanning-alerts-for-an-enterprise)

## All Parameters for "List secret scanning alerts for an enterprise"

### Path Parameters

- `enterprise` (string, required): The slug version of the enterprise name. You can also substitute this value with the enterprise id.
### Query Parameters

- `state` (string): Set to `open` or `resolved` to only list secret scanning alerts in a specific state.
- `secret_type` (string): A comma-separated list of secret types to return. By default all secret types are returned.
See "[Supported secret scanning patterns](https://docs.github.com/code-security/secret-scanning/introduction/supported-secret-scanning-patterns#supported-secrets)"
for a complete list of secret types.
- `resolution` (string): A comma-separated list of resolutions. Only secret scanning alerts with one of these resolutions are listed. Valid resolutions are `false_positive`, `wont_fix`, `revoked`, `pattern_edited`, `pattern_deleted` or `used_in_tests`.
- `sort` (string): The property to sort the results by. `created` means when the alert was created. `updated` means when the alert was updated or resolved.
- `direction` (string): The direction to sort the results by.
- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `before` (string): A cursor, as given in the [Link header](https://docs.github.com/rest/guides/using-pagination-in-the-rest-api#using-link-headers). If specified, the query only searches for results before this cursor. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `after` (string): A cursor, as given in the [Link header](https://docs.github.com/rest/guides/using-pagination-in-the-rest-api#using-link-headers). If specified, the query only searches for results after this cursor. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `validity` (string): A comma-separated list of validities that, when present, will return alerts that match the validities in this list. Valid options are `active`, `inactive`, and `unknown`.

## Operation Description

Lists secret scanning alerts for eligible repositories in an enterprise, from newest to oldest.

Alerts are only returned for organizations in the enterprise for which the authenticated user is an organization owner or a [security manager](https://docs.github.com/organizations/managing-peoples-access-to-your-organization-with-roles/managing-security-managers-in-your-organization).

The authenticated user must be a member of the enterprise in order to use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `repo` scope or `security_events` scope to use this endpoint.
