# Get a classroom

Gets a GitHub Classroom classroom for the current user. Classroom will only be returned if the current user is an administrator of the GitHub Classroom.

## Operation Object

```json
{
    "summary": "Get a classroom",
    "description": "Gets a GitHub Classroom classroom for the current user. Classroom will only be returned if the current user is an administrator of the GitHub Classroom.",
    "tags": [
        "classroom"
    ],
    "operationId": "classroom/get-a-classroom",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/classroom/classroom#get-a-classroom"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/classroom-id"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/classroom"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/classroom"
                        }
                    }
                }
            }
        },
        "404": {
            "$ref": "#/components/responses/not_found"
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

### `#/components/parameters/classroom-id`

```json
{
    "name": "classroom_id",
    "description": "The unique identifier of the classroom.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "integer"
    }
}
```

### `#/components/schemas/classroom`

```json
{
    "title": "Classroom",
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
            "description": "Whether classroom is archived.",
            "type": "boolean",
            "example": false
        },
        "organization": {
            "$ref": "#/components/schemas/simple-classroom-organization"
        },
        "url": {
            "description": "The URL of the classroom on GitHub Classroom.",
            "type": "string",
            "example": "https://classroom.github.com/classrooms/1-programming-elixir"
        }
    },
    "required": [
        "id",
        "name",
        "archived",
        "organization",
        "url"
    ]
}
```

### `#/components/examples/classroom`

```json
{
    "value": {
        "id": 1296269,
        "name": "Programming Elixir",
        "archived": "false,",
        "organization": {
            "id": 1,
            "login": "programming-elixir",
            "node_id": "MDEyOk9yZ2FuaXphdGlvbjE=",
            "html_url": "https://github.com/programming-elixir",
            "name": "Learn how to build fault tolerant applications",
            "avatar_url": "https://avatars.githubusercontent.com/u/9919?v=4"
        },
        "url": "https://classroom.github.com/classrooms/1-programming-elixir"
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