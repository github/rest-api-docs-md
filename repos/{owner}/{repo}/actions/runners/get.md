# List self-hosted runners for a repository

`get /repos/{owner}/{repo}/actions/runners`

Lists all self-hosted runners configured in a repository.

Authenticated users must have admin access to the repository to use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "List self-hosted runners for a repository",
    "description": "Lists all self-hosted runners configured in a repository.\n\nAuthenticated users must have admin access to the repository to use this endpoint.\n\nOAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.",
    "tags": [
        "actions"
    ],
    "operationId": "actions/list-self-hosted-runners-for-repo",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/actions/self-hosted-runners#list-self-hosted-runners-for-a-repository"
    },
    "parameters": [
        {
            "name": "name",
            "description": "The name of a self-hosted runner.",
            "in": "query",
            "schema": {
                "type": "string"
            }
        },
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
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
                        "type": "object",
                        "required": [
                            "total_count",
                            "runners"
                        ],
                        "properties": {
                            "total_count": {
                                "type": "integer"
                            },
                            "runners": {
                                "type": "array",
                                "items": {
                                    "$ref": "#/components/schemas/runner"
                                }
                            }
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/runner-paginated"
                        }
                    }
                }
            },
            "headers": {
                "Link": {
                    "$ref": "#/components/headers/link"
                }
            }
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "actions",
        "subcategory": "self-hosted-runners"
    }
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

### `#/components/schemas/runner`

```json
{
    "title": "Self hosted runners",
    "description": "A self hosted runner",
    "type": "object",
    "properties": {
        "id": {
            "description": "The id of the runner.",
            "type": "integer",
            "example": 5
        },
        "runner_group_id": {
            "description": "The id of the runner group.",
            "type": "integer",
            "example": 1
        },
        "name": {
            "description": "The name of the runner.",
            "type": "string",
            "example": "iMac"
        },
        "os": {
            "description": "The Operating System of the runner.",
            "type": "string",
            "example": "macos"
        },
        "status": {
            "description": "The status of the runner.",
            "type": "string",
            "example": "online"
        },
        "busy": {
            "type": "boolean"
        },
        "labels": {
            "type": "array",
            "items": {
                "$ref": "#/components/schemas/runner-label"
            }
        }
    },
    "required": [
        "id",
        "name",
        "os",
        "status",
        "busy",
        "labels"
    ]
}
```

### `#/components/examples/runner-paginated`

```json
{
    "value": {
        "total_count": 2,
        "runners": [
            {
                "id": 23,
                "name": "linux_runner",
                "os": "linux",
                "status": "online",
                "busy": true,
                "labels": [
                    {
                        "id": 5,
                        "name": "self-hosted",
                        "type": "read-only"
                    },
                    {
                        "id": 7,
                        "name": "X64",
                        "type": "read-only"
                    },
                    {
                        "id": 11,
                        "name": "Linux",
                        "type": "read-only"
                    }
                ]
            },
            {
                "id": 24,
                "name": "mac_runner",
                "os": "macos",
                "status": "offline",
                "busy": false,
                "labels": [
                    {
                        "id": 5,
                        "name": "self-hosted",
                        "type": "read-only"
                    },
                    {
                        "id": 7,
                        "name": "X64",
                        "type": "read-only"
                    },
                    {
                        "id": 20,
                        "name": "macOS",
                        "type": "read-only"
                    },
                    {
                        "id": 21,
                        "name": "no-gpu",
                        "type": "custom"
                    }
                ]
            }
        ]
    }
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