# List labels for a self-hosted runner for a repository

Lists all labels for a self-hosted runner configured in a repository.

Authenticated users must have admin access to the repository to use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "List labels for a self-hosted runner for a repository",
    "description": "Lists all labels for a self-hosted runner configured in a repository.\n\nAuthenticated users must have admin access to the repository to use this endpoint.\n\nOAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.",
    "tags": [
        "actions"
    ],
    "operationId": "actions/list-labels-for-self-hosted-runner-for-repo",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/actions/self-hosted-runners#list-labels-for-a-self-hosted-runner-for-a-repository"
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
            "$ref": "#/components/responses/actions_runner_labels"
        },
        "404": {
            "$ref": "#/components/responses/not_found"
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

### `#/components/responses/actions_runner_labels`

```json
{
    "description": "Response",
    "content": {
        "application/json": {
            "schema": {
                "type": "object",
                "required": [
                    "total_count",
                    "labels"
                ],
                "properties": {
                    "total_count": {
                        "type": "integer"
                    },
                    "labels": {
                        "type": "array",
                        "items": {
                            "$ref": "#/components/schemas/runner-label"
                        }
                    }
                }
            },
            "examples": {
                "default": {
                    "$ref": "#/components/examples/runner-labels"
                }
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