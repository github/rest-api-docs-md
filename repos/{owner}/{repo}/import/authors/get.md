# Get commit authors

Each type of source control system represents authors in a different way. For example, a Git commit author has a display name and an email address, but a Subversion commit author just has a username. The GitHub Importer will make the author information valid, but the author might not be correct. For example, it will change the bare Subversion username `hubot` into something like `hubot <hubot@12341234-abab-fefe-8787-fedcba987654>`.

This endpoint and the [Map a commit author](https://docs.github.com/rest/migrations/source-imports#map-a-commit-author) endpoint allow you to provide correct Git author information.

**Warning:** Due to very low levels of usage and available alternatives, this endpoint is deprecated and will no longer be available from 00:00 UTC on April 12, 2024. For more details and alternatives, see the [changelog](https://gh.io/source-imports-api-deprecation).

## Operation Object

```json
{
    "summary": "Get commit authors",
    "description": "Each type of source control system represents authors in a different way. For example, a Git commit author has a display name and an email address, but a Subversion commit author just has a username. The GitHub Importer will make the author information valid, but the author might not be correct. For example, it will change the bare Subversion username `hubot` into something like `hubot <hubot@12341234-abab-fefe-8787-fedcba987654>`.\n\nThis endpoint and the [Map a commit author](https://docs.github.com/rest/migrations/source-imports#map-a-commit-author) endpoint allow you to provide correct Git author information.\n\n**Warning:** Due to very low levels of usage and available alternatives, this endpoint is deprecated and will no longer be available from 00:00 UTC on April 12, 2024. For more details and alternatives, see the [changelog](https://gh.io/source-imports-api-deprecation).",
    "tags": [
        "migrations"
    ],
    "operationId": "migrations/get-commit-authors",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/migrations/source-imports#get-commit-authors"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "$ref": "#/components/parameters/since-user"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "type": "array",
                        "items": {
                            "$ref": "#/components/schemas/porter-author"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/porter-author-items"
                        }
                    }
                }
            }
        },
        "404": {
            "$ref": "#/components/responses/not_found"
        },
        "503": {
            "$ref": "#/components/responses/porter_maintenance"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "migrations",
        "subcategory": "source-imports",
        "deprecationDate": "2023-10-12",
        "removalDate": "2024-04-12"
    },
    "deprecated": true
}
```

## References

### `#/components/parameters/owner`

```json
{
    "name": "owner",
    "description": "The account owner of the repository. The name is not case sensitive.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "string"
    }
}
```

### `#/components/parameters/repo`

```json
{
    "name": "repo",
    "description": "The name of the repository without the `.git` extension. The name is not case sensitive.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "string"
    }
}
```

### `#/components/parameters/since-user`

```json
{
    "name": "since",
    "description": "A user ID. Only return users with an ID greater than this ID.",
    "in": "query",
    "required": false,
    "schema": {
        "type": "integer"
    }
}
```

### `#/components/schemas/porter-author`

```json
{
    "title": "Porter Author",
    "description": "Porter Author",
    "type": "object",
    "properties": {
        "id": {
            "type": "integer"
        },
        "remote_id": {
            "type": "string"
        },
        "remote_name": {
            "type": "string"
        },
        "email": {
            "type": "string"
        },
        "name": {
            "type": "string"
        },
        "url": {
            "type": "string",
            "format": "uri"
        },
        "import_url": {
            "type": "string",
            "format": "uri"
        }
    },
    "required": [
        "id",
        "remote_id",
        "remote_name",
        "email",
        "name",
        "url",
        "import_url"
    ]
}
```

### `#/components/examples/porter-author-items`

```json
{
    "value": [
        {
            "id": 2268557,
            "remote_id": "nobody@fc7da526-431c-80fe-3c8c-c148ff18d7ef",
            "remote_name": "nobody",
            "email": "hubot@github.com",
            "name": "Hubot",
            "url": "https://api.github.com/repos/octocat/socm/import/authors/2268557",
            "import_url": "https://api.github.com/repos/octocat/socm/import"
        },
        {
            "id": 2268558,
            "remote_id": "svner@fc7da526-431c-80fe-3c8c-c148ff18d7ef",
            "remote_name": "svner",
            "email": "svner@fc7da526-431c-80fe-3c8c-c148ff18d7ef",
            "name": "svner",
            "url": "https://api.github.com/repos/octocat/socm/import/authors/2268558",
            "import_url": "https://api.github.com/repos/octocat/socm/import"
        },
        {
            "id": 2268559,
            "remote_id": "svner@example.com@fc7da526-431c-80fe-3c8c-c148ff18d7ef",
            "remote_name": "svner@example.com",
            "email": "svner@example.com@fc7da526-431c-80fe-3c8c-c148ff18d7ef",
            "name": "svner@example.com",
            "url": "https://api.github.com/repos/octocat/socm/import/authors/2268559",
            "import_url": "https://api.github.com/repos/octocat/socm/import"
        }
    ]
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

### `#/components/responses/porter_maintenance`

```json
{
    "description": "Unavailable due to service under maintenance.",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/basic-error"
            }
        }
    }
}
```