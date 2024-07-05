# Get a self-hosted runner for a repository

Gets a specific self-hosted runner configured in a repository.

Authenticated users must have admin access to the repository to use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "Get a self-hosted runner for a repository",
    "description": "Gets a specific self-hosted runner configured in a repository.\n\nAuthenticated users must have admin access to the repository to use this endpoint.\n\nOAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.",
    "tags": [
        "actions"
    ],
    "operationId": "actions/get-self-hosted-runner-for-repo",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/actions/self-hosted-runners#get-a-self-hosted-runner-for-a-repository"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "$ref": "#/components/parameters/runner-id"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/runner"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/runner"
                        }
                    }
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

### `#/components/parameters/runner-id`

```json
{
    "name": "runner_id",
    "description": "Unique identifier of the self-hosted runner.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "integer"
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

### `#/components/examples/runner`

```json
{
    "value": {
        "id": 23,
        "name": "MBP",
        "os": "macos",
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
}
```