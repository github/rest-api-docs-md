# List repositories for a user migration

`GET /user/migrations/{migration_id}/repositories`

[API method documentation](https://docs.github.com/rest/migrations/users#list-repositories-for-a-user-migration)

## All Parameters for "List repositories for a user migration"

### Path Parameters

- `migration_id` (integer, required): The unique identifier of the migration.
### Query Parameters

- `per_page` (integer): The number of results per page (max 100). For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."
- `page` (integer): The page number of the results to fetch. For more information, see "[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api)."

## Operation Description

Lists all the repositories for this user migration.
