# List classrooms

Lists GitHub Classroom classrooms for the current user. Classrooms will only be returned if the current user is an administrator of one or more GitHub Classrooms.

## Operation Object

```json
{
    "summary": "List classrooms",
    "description": "Lists GitHub Classroom classrooms for the current user. Classrooms will only be returned if the current user is an administrator of one or more GitHub Classrooms.",
    "tags": [
        "classroom"
    ],
    "operationId": "classroom/list-classrooms",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/classroom/classroom#list-classrooms"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/page"
        },
        {
            "$ref": "#/components/parameters/per-page"
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
                            "$ref": "#/components/schemas/simple-classroom"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/simple-classroom"
                        }
                    }
                }
            }
        }
    },
    "x-github": {
        "enabledForGitHubApps": true,
        "category": "classroom",
        "subcategory": "classroom"
    }
}
```

## References

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

### `#/components/schemas/simple-classroom`

```json
{
    "title": "Simple Classroom",
    "description": "A GitHub Classroom classroom",
    "type": "object",
    "properties": {
        "id": {
            "description": "Unique identifier of the classroom.",
            "example": 42,
            "type": "integer"
        },
        "name": {
            "description": "The name of the classroom.",
            "type": "string",
            "example": "Programming Elixir"
        },
        "archived": {
            "description": "Returns whether classroom is archived or not.",
            "type": "boolean",
            "example": false
        },
        "url": {
            "description": "The url of the classroom on GitHub Classroom.",
            "type": "string",
            "example": "https://classroom.github.com/classrooms/1-programming-elixir"
        }
    },
    "required": [
        "id",
        "name",
        "archived",
        "url"
    ]
}
```

### `#/components/examples/simple-classroom`

```json
{
    "value": {
        "id": 1296269,
        "name": "Programming Elixir",
        "archived": "false,",
        "url": "https://classroom.github.com/classrooms/1-programming-elixir"
    }
}
```