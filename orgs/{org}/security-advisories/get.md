# List repository security advisories for an organization

`GET /orgs/{org}/security-advisories`

[API method documentation](https://docs.github.com/rest/security-advisories/repository-advisories#list-repository-security-advisories-for-an-organization)

## All Parameters for "List repository security advisories for an organization"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.
### Query Parameters

- `direction` (string): The direction to sort the results by.
- `sort` (string): The property to sort the results by.
- `before` (string): A cursor, as given in the [Link header](https://docs.github.com/rest/guides/using-pagination-in-the-rest-api#using-link-headers). If specified, the query only searches for results before this cursor. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `after` (string): A cursor, as given in the [Link header](https://docs.github.com/rest/guides/using-pagination-in-the-rest-api#using-link-headers). If specified, the query only searches for results after this cursor. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `per_page` (integer): The number of advisories to return per page. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `state` (string): Filter by the state of the repository advisories. Only advisories of this state will be returned.

## Operation Description

Lists repository security advisories for an organization.

The authenticated user must be an owner or security manager for the organization to use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `repo` or `repository_advisories:write` scope to use this endpoint.
