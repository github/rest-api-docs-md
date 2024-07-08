# Get repositories associated with a code security configuration

`GET /orgs/{org}/code-security/configurations/{configuration_id}/repositories`

Lists the repositories associated with a code security configuration in an organization.

The authenticated user must be an administrator or security manager for the organization to use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `write:org` scope to use this endpoint.

[API method documentation](https://docs.github.com/rest/code-security/configurations#get-repositories-associated-with-a-code-security-configuration)

## All Parameters for "Get repositories associated with a code security configuration"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.
- `configuration_id` (integer, required): The unique identifier of the code security configuration.
### Query Parameters

- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `before` (string): A cursor, as given in the [Link header](https://docs.github.com/rest/guides/using-pagination-in-the-rest-api#using-link-headers). If specified, the query only searches for results before this cursor. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `after` (string): A cursor, as given in the [Link header](https://docs.github.com/rest/guides/using-pagination-in-the-rest-api#using-link-headers). If specified, the query only searches for results after this cursor. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `status` (string): A comma-separated list of statuses. If specified, only repositories with these attachment statuses will be returned.

Can be: `all`, `attached`, `attaching`, `detached`, `enforced`, `failed`, `updating`