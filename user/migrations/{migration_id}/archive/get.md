# Download a user migration archive

`GET /user/migrations/{migration_id}/archive`

Fetches the URL to download the migration archive as a `tar.gz` file. Depending on the resources your repository uses, the migration archive can contain JSON files with data for these objects:

*   attachments
*   bases
*   commit\_comments
*   issue\_comments
*   issue\_events
*   issues
*   milestones
*   organizations
*   projects
*   protected\_branches
*   pull\_request\_reviews
*   pull\_requests
*   releases
*   repositories
*   review\_comments
*   schema
*   users

The archive will also contain an `attachments` directory that includes all attachment files uploaded to GitHub.com and a `repositories` directory that contains the repository's Git data.

[API method documentation](https://docs.github.com/rest/migrations/users#download-a-user-migration-archive)

## All Parameters for "Download a user migration archive"

### Path Parameters

- `migration_id` (integer, required): The unique identifier of the migration.