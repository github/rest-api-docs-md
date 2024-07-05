# Download an organization migration archive

Fetches the URL to a migration archive.

## Operation Object

```json
{
    "summary": "Download an organization migration archive",
    "description": "Fetches the URL to a migration archive.",
    "tags": [
        "migrations"
    ],
    "operationId": "migrations/download-archive-for-org",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/migrations/orgs#download-an-organization-migration-archive"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/org"
        },
        {
            "$ref": "#/components/parameters/migration-id"
        }
    ],
    "responses": {
        "302": {
            "description": "Response"
        },
        "404": {
            "$ref": "#/components/responses/not_found"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": false,
        "category": "migrations",
        "subcategory": "orgs"
    }
}
```

## References

### `#/components/parameters/org`

```json
{
    "name": "org",
    "description": "The organization name. The name is not case sensitive.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "string"
    }
}
```

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

### `#/components/responses/not_found`

```json
{
    "description": "Resource not found",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/basic-error"
            }
        }
    }
}
```