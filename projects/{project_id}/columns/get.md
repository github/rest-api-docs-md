# List project columns

`get /projects/{project_id}/columns`

Lists the project columns in a project.

## Operation Object

```json
{
    "summary": "List project columns",
    "description": "Lists the project columns in a project.",
    "tags": [
        "projects"
    ],
    "operationId": "projects/list-columns",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/projects/columns#list-project-columns"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/project-id"
        },
        {
            "$ref": "#/components/parameters/per-page"
        },
        {
            "$ref": "#/components/parameters/page"
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
                            "$ref": "#/components/schemas/project-column"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/project-column-items"
                        }
                    }
                }
            },
            "headers": {
                "Link": {
                    "$ref": "#/components/headers/link"
                }
            }
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
        "enabledForGitHubApps": true,
        "category": "projects",
        "subcategory": "columns"
    }
}
```

## References

### `#/components/parameters/project-id`

```json
{
    "name": "project_id",
    "description": "The unique identifier of the project.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "integer"
    }
}
```

### `#/components/parameters/per-page`

```json
{
    "name": "per_page",
    "description": "The number of results per page (max 100). For more information, see \"[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api).\"",
    "in": "query",
    "schema": {
        "type": "integer",
        "default": 30
    }
}
```

### `#/components/parameters/page`

```json
{
    "name": "page",
    "description": "The page number of the results to fetch. For more information, see \"[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api).\"",
    "in": "query",
    "schema": {
        "type": "integer",
        "default": 1
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

### `#/components/examples/project-column-items`

```json
{
    "value": [
        {
            "url": "https://api.github.com/projects/columns/367",
            "project_url": "https://api.github.com/projects/120",
            "cards_url": "https://api.github.com/projects/columns/367/cards",
            "id": 367,
            "node_id": "MDEzOlByb2plY3RDb2x1bW4zNjc=",
            "name": "To Do",
            "created_at": "2016-09-05T14:18:44Z",
            "updated_at": "2016-09-05T14:22:28Z"
        }
    ]
}
```

### `#/components/headers/link`

```json
{
    "example": "<https://api.github.com/resource?page=2>; rel=\"next\", <https://api.github.com/resource?page=5>; rel=\"last\"",
    "schema": {
        "type": "string"
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