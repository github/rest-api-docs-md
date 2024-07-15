# Get an organization migration status

`GET /orgs/{org}/migrations/{migration_id}`

[API method documentation](https://docs.github.com/rest/migrations/orgs#get-an-organization-migration-status)

## All Parameters for "Get an organization migration status"

### Path Parameters

- `org` (string, required): The organization name. The name is not case sensitive.
- `migration_id` (integer, required): The unique identifier of the migration.
### Query Parameters

- `exclude` (array): Exclude attributes from the API response to improve performance

## Operation Description

Fetches the status of a migration.

The `state` of a migration can be one of the following values:

*   `pending`, which means the migration hasn't started yet.
*   `exporting`, which means the migration is in progress.
*   `exported`, which means the migration finished successfully.
*   `failed`, which means the migration failed.
