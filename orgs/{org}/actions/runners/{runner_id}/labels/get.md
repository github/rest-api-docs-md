# List labels for a self-hosted runner for an organization

Lists all labels for a self-hosted runner configured in an organization.

Authenticated users must have admin access to the organization to use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `admin:org` scope to use this endpoint. If the repository is private, the `repo` scope is also required.

## Operation Object

```json
{
    "summary": "List labels for a self-hosted runner for an organization",
    "description": "Lists all labels for a self-hosted runner configured in an organization.\n\nAuthenticated users must have admin access to the organization to use this endpoint.\n\nOAuth app tokens and personal access tokens (classic) need the `admin:org` scope to use this endpoint. If the repository is private, the `repo` scope is also required.",
    "tags": [
        "actions"
    ],
    "operationId": "actions/list-labels-for-self-hosted-runner-for-org",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/actions/self-hosted-runners#list-labels-for-a-self-hosted-runner-for-an-organization"
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