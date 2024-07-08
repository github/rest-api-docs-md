# Get a user migration status

`GET /user/migrations/{migration_id}`

Fetches a single user migration. The response includes the `state` of the migration, which can be one of the following values:

*   `pending` - the migration hasn't started yet.
*   `exporting` - the migration is in progress.
*   `exported` - the migration finished successfully.
*   `failed` - the migration failed.

Once the migration has been `exported` you can [download the migration archive](https://docs.github.com/rest/migrations/users#download-a-user-migration-archive).

[API method documentation](https://docs.github.com/rest/migrations/users#get-a-user-migration-status)

## All Parameters for "Get a user migration status"

### Path Parameters

- `migration_id` (integer, required): The unique identifier of the migration.
### Query Parameters

- `exclude` (array)