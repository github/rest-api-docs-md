# List repositories in an organization migration

`GET /orgs/{org}/migrations/{migration_id}/repositories`

List all the repositories for this organization migration.

[API method documentation](https://docs.github.com/rest/migrations/orgs#list-repositories-in-an-organization-migration)

## All Parameters for "List repositories in an organization migration"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.
- `migration_id` (integer, required): The unique identifier of the migration.
### Query Parameters

- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."