# List self-hosted runners for an organization

`get /orgs/{org}/actions/runners`

Lists all self-hosted runners configured in an organization.

Authenticated users must have admin access to the organization to use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `admin:org` scope to use this endpoint. If the repository is private, the `repo` scope is also required.

## Operation Object

```json
{
    "summary": "List self-hosted runners for an organization",
    "description": "Lists all self-hosted runners configured in an organization.\n\nAuthenticated users must have admin access to the organization to use this endpoint.\n\nOAuth app tokens and personal access tokens (classic) need the `admin:org` scope to use this endpoint. If the repository is private, the `repo` scope is also required.",
    "tags": [
        "actions"
    ],
    "operationId": "actions/list-self-hosted-runners-for-org",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/actions/self-hosted-runners#list-self-hosted-runners-for-an-organization"
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
            "$ref": "#/components/parameters/org"
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