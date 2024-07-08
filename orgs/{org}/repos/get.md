# List organization repositories

`GET /orgs/{org}/repos`

Lists repositories for the specified organization.

**Note:** In order to see the `security_and_analysis` block for a repository you must have admin permissions for the repository or be an owner or security manager for the organization that owns the repository. For more information, see "[Managing security managers in your organization](https://docs.github.com/organizations/managing-peoples-access-to-your-organization-with-roles/managing-security-managers-in-your-organization)."

[API method documentation](https://docs.github.com/rest/repos/repos#list-organization-repositories)

## All Parameters for "List organization repositories"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.
### Query Parameters

- `type` (string): Specifies the types of repositories you want returned.
- `sort` (string): The property to sort the results by.
- `direction` (string): The order to sort by. Default: `asc` when using `full_name`, otherwise `desc`.
- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."