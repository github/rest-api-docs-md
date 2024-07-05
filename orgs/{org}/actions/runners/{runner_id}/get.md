# Get a self-hosted runner for an organization

`get /orgs/{org}/actions/runners/{runner_id}`

Gets a specific self-hosted runner configured in an organization.

Authenticated users must have admin access to the organization to use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `admin:org` scope to use this endpoint. If the repository is private, the `repo` scope is also required.

## Operation Object

```json
{
    "summary": "Get a self-hosted runner for an organization",
    "description": "Gets a specific self-hosted runner configured in an organization.\n\nAuthenticated users must have admin access to the organization to use this endpoint.\n\nOAuth app tokens and personal access tokens (classic) need the `admin:org` scope to use this endpoint. If the repository is private, the `repo` scope is also required.",
    "tags": [
        "actions"
    ],
    "operationId": "actions/get-self-hosted-runner-for-org",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/actions/self-hosted-runners#get-a-self-hosted-runner-for-an-organization"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/org"
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