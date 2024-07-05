# Get a project column

Gets information about a project column.

## Operation Object

```json
{
    "summary": "Get a project column",
    "description": "Gets information about a project column.",
    "tags": [
        "projects"
    ],
    "operationId": "projects/get-column",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/projects/columns#get-a-project-column"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/column-id"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/project-column"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/project-column"
                        }
                    }
                }
            }
        },
        "304": {
            "$ref": "#/components/responses/not_modified"
        },
        "403": {
            "$ref": "#/components/responses/forbidden"
        },
        "404": {
            "$ref": "#/components/responses/not_found"
        },
        "401": {
            "$ref": "#/components/responses/requires_authentication"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "projects",
        "subcategory": "columns"
    }
}
```

## References

### `#/components/parameters/column-id`

```json
{
    "name": "column_id",
    "description": "The unique identifier of the column.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "integer"
    }
}
```

### `#/components/schemas/project-column`

```json
{
    "title": "Project Column",
    "description": "Project columns contain cards of work.",
    "type": "object",
    "properties": {
        "url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/projects/columns/367"
        },
        "project_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/projects/120"
        },
        "cards_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/projects/columns/367/cards"
        },
        "id": {
            "description": "The unique identifier of the project column",
            "example": 42,
            "type": "integer"
        },
        "node_id": {
            "type": "string",
            "example": "MDEzOlByb2plY3RDb2x1bW4zNjc="
        },
        "name": {
            "description": "Name of the project column",
            "example": "Remaining tasks",
            "type": "string"
        },
        "created_at": {
            "type": "string",
            "format": "date-time",
            "example": "2016-09-05T14:18:44Z"
        },
        "updated_at": {
            "type": "string",
            "format": "date-time",
            "example": "2016-09-05T14:22:28Z"
        }
    },
    "required": [
        "id",
        "node_id",
        "url",
        "project_url",
        "cards_url",
        "name",
        "created_at",
        "updated_at"
    ]
}
```

### `#/components/examples/project-column`

```json
{
    "value": {
        "url": "https://api.github.com/projects/columns/367",
        "project_url": "https://api.github.com/projects/120",
        "cards_url": "https://api.github.com/projects/columns/367/cards",
        "id": 367,
        "node_id": "MDEzOlByb2plY3RDb2x1bW4zNjc=",
        "name": "To Do",
        "created_at": "2016-09-05T14:18:44Z",
        "updated_at": "2016-09-05T14:22:28Z"
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