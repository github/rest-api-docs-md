# List project cards

`get /projects/columns/{column_id}/cards`

Lists the project cards in a project.

## Operation Object

```json
{
    "summary": "List project cards",
    "description": "Lists the project cards in a project.",
    "tags": [
        "projects"
    ],
    "operationId": "projects/list-cards",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/projects/cards#list-project-cards"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/column-id"
        },
        {
            "name": "archived_state",
            "description": "Filters the project cards that are returned by the card's state.",
            "in": "query",
            "required": false,
            "schema": {
                "type": "string",
                "enum": [
                    "all",
                    "archived",
                    "not_archived"
                ],
                "default": "not_archived"
            }
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
                            "$ref": "#/components/schemas/project-card"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/project-card-items"
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
        "subcategory": "cards"
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

### `#/components/schemas/project-card`

```json
{
    "title": "Project Card",
    "description": "Project cards represent a scope of work.",
    "type": "object",
    "properties": {
        "url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/projects/columns/cards/1478"
        },
        "id": {
            "description": "The project card's ID",
            "example": 42,
            "type": "integer",
            "format": "int64"
        },
        "node_id": {
            "type": "string",
            "example": "MDExOlByb2plY3RDYXJkMTQ3OA=="
        },
        "note": {
            "type": "string",
            "example": "Add payload for delete Project column",
            "nullable": true
        },
        "creator": {
            "$ref": "#/components/schemas/nullable-simple-user"
        },
        "created_at": {
            "type": "string",
            "format": "date-time",
            "example": "2016-09-05T14:21:06Z"
        },
        "updated_at": {
            "type": "string",
            "format": "date-time",
            "example": "2016-09-05T14:20:22Z"
        },
        "archived": {
            "description": "Whether or not the card is archived",
            "example": false,
            "type": "boolean"
        },
        "column_name": {
            "type": "string"
        },
        "project_id": {
            "type": "string"
        },
        "column_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/projects/columns/367"
        },
        "content_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/repos/api-playground/projects-test/issues/3"
        },
        "project_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/projects/120"
        }
    },
    "required": [
        "id",
        "node_id",
        "note",
        "url",
        "column_url",
        "project_url",
        "creator",
        "created_at",
        "updated_at"
    ]
}
```

### `#/components/examples/project-card-items`

```json
{
    "value": [
        {
            "url": "https://api.github.com/projects/columns/cards/1478",
            "id": 1478,
            "node_id": "MDExOlByb2plY3RDYXJkMTQ3OA==",
            "note": "Add payload for delete Project column",
            "creator": {
                "login": "octocat",
                "id": 1,
                "node_id": "MDQ6VXNlcjE=",
                "avatar_url": "https://github.com/images/error/octocat_happy.gif",
                "gravatar_id": "",
                "url": "https://api.github.com/users/octocat",
                "html_url": "https://github.com/octocat",
                "followers_url": "https://api.github.com/users/octocat/followers",
                "following_url": "https://api.github.com/users/octocat/following{/other_user}",
                "gists_url": "https://api.github.com/users/octocat/gists{/gist_id}",
                "starred_url": "https://api.github.com/users/octocat/starred{/owner}{/repo}",
                "subscriptions_url": "https://api.github.com/users/octocat/subscriptions",
                "organizations_url": "https://api.github.com/users/octocat/orgs",
                "repos_url": "https://api.github.com/users/octocat/repos",
                "events_url": "https://api.github.com/users/octocat/events{/privacy}",
                "received_events_url": "https://api.github.com/users/octocat/received_events",
                "type": "User",
                "site_admin": false
            },
            "created_at": "2016-09-05T14:21:06Z",
            "updated_at": "2016-09-05T14:20:22Z",
            "archived": false,
            "column_url": "https://api.github.com/projects/columns/367",
            "content_url": "https://api.github.com/repos/api-playground/projects-test/issues/3",
            "project_url": "https://api.github.com/projects/120"
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