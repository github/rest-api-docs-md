# Get code security configurations for an organization

`GET /orgs/{org}/code-security/configurations`

[API method documentation](https://docs.github.com/rest/code-security/configurations#get-code-security-configurations-for-an-organization)

## All Parameters for "Get code security configurations for an organization"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.
### Query Parameters

- `target_type` (string): The target type of the code security configuration
- `per_page` (integer): 'The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."'

- `before` (string): A cursor, as given in the [Link header](https://docs.github.com/rest/guides/using-pagination-in-the-rest-api#using-link-headers). If specified, the query only searches for results before this cursor. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `after` (string): A cursor, as given in the [Link header](https://docs.github.com/rest/guides/using-pagination-in-the-rest-api#using-link-headers). If specified, the query only searches for results after this cursor. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."

## Operation Description

Lists all code security configurations available in an organization.

The authenticated user must be an administrator or security manager for the organization to use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `write:org` scope to use this endpoint.
