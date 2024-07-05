# Download a user migration archive

`get /user/migrations/{migration_id}/archive`

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

## Operation Object

```json
{
    "summary": "Download a user migration archive",
    "description": "Fetches the URL to download the migration archive as a `tar.gz` file. Depending on the resources your repository uses, the migration archive can contain JSON files with data for these objects:\n\n*   attachments\n*   bases\n*   commit\\_comments\n*   issue\\_comments\n*   issue\\_events\n*   issues\n*   milestones\n*   organizations\n*   projects\n*   protected\\_branches\n*   pull\\_request\\_reviews\n*   pull\\_requests\n*   releases\n*   repositories\n*   review\\_comments\n*   schema\n*   users\n\nThe archive will also contain an `attachments` directory that includes all attachment files uploaded to GitHub.com and a `repositories` directory that contains the repository's Git data.",
    "tags": [
        "migrations"
    ],
    "operationId": "migrations/get-archive-for-authenticated-user",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/migrations/users#download-a-user-migration-archive"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/migration-id"
        }
    ],
    "responses": {
        "302": {
            "description": "Response"
        },
        "304": {
            "$ref": "#/components/responses/not_modified"
        },
        "403": {
            "$ref": "#/components/responses/forbidden"
        },
        "401": {
            "$ref": "#/components/responses/requires_authentication"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": false,
        "category": "migrations",
        "subcategory": "users"
    }
}
```

## References

### `#/components/parameters/migration-id`

```json
{
    "name": "migration_id",
    "description": "The unique identifier of the migration.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "integer"
    }
}
```

### `#/components/responses/not_modified`

```json
{
    "description": "Not modified"
}
```

### `#/components/responses/forbidden`

```json
{
    "description": "Forbidden",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/basic-error"
            }
        }
    }
}
```

### `#/components/responses/requires_authentication`

```json
{
    "description": "Requires authentication",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/basic-error"
            }
        }
    }
}
```