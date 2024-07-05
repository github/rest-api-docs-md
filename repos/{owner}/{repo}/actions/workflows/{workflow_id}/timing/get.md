# Get workflow usage

`get /repos/{owner}/{repo}/actions/workflows/{workflow_id}/timing`

Gets the number of billable minutes used by a specific workflow during the current billing cycle. Billable minutes only apply to workflows in private repositories that use GitHub-hosted runners. Usage is listed for each GitHub-hosted runner operating system in milliseconds. Any job re-runs are also included in the usage. The usage does not include the multiplier for macOS and Windows runners and is not rounded up to the nearest whole minute. For more information, see "[Managing billing for GitHub Actions](https://docs.github.com/github/setting-up-and-managing-billing-and-payments-on-github/managing-billing-for-github-actions)".

You can replace `workflow_id` with the workflow file name. For example, you could use `main.yaml`.

Anyone with read access to the repository can use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint with a private repository.

## Operation Object

```json
{
    "summary": "Get workflow usage",
    "description": "Gets the number of billable minutes used by a specific workflow during the current billing cycle. Billable minutes only apply to workflows in private repositories that use GitHub-hosted runners. Usage is listed for each GitHub-hosted runner operating system in milliseconds. Any job re-runs are also included in the usage. The usage does not include the multiplier for macOS and Windows runners and is not rounded up to the nearest whole minute. For more information, see \"[Managing billing for GitHub Actions](https://docs.github.com/github/setting-up-and-managing-billing-and-payments-on-github/managing-billing-for-github-actions)\".\n\nYou can replace `workflow_id` with the workflow file name. For example, you could use `main.yaml`.\n\nAnyone with read access to the repository can use this endpoint.\n\nOAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint with a private repository.",
    "tags": [
        "actions"
    ],
    "operationId": "actions/get-workflow-usage",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/actions/workflows#get-workflow-usage"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "$ref": "#/components/parameters/workflow-id"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/workflow-usage"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/workflow-usage"
                        }
                    }
                }
            }
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": false,
        "category": "actions",
        "subcategory": "workflows"
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

### `#/components/parameters/workflow-id`

```json
{
    "name": "workflow_id",
    "in": "path",
    "description": "The ID of the workflow. You can also pass the workflow file name as a string.",
    "required": true,
    "schema": {
        "oneOf": [
            {
                "type": "integer"
            },
            {
                "type": "string"
            }
        ]
    }
}
```

### `#/components/schemas/workflow-usage`

```json
{
    "title": "Workflow Usage",
    "description": "Workflow Usage",
    "type": "object",
    "properties": {
        "billable": {
            "type": "object",
            "properties": {
                "UBUNTU": {
                    "type": "object",
                    "properties": {
                        "total_ms": {
                            "type": "integer"
                        }
                    }
                },
                "MACOS": {
                    "type": "object",
                    "properties": {
                        "total_ms": {
                            "type": "integer"
                        }
                    }
                },
                "WINDOWS": {
                    "type": "object",
                    "properties": {
                        "total_ms": {
                            "type": "integer"
                        }
                    }
                }
            }
        }
    },
    "required": [
        "billable"
    ]
}
```

### `#/components/examples/workflow-usage`

```json
{
    "value": {
        "billable": {
            "UBUNTU": {
                "total_ms": 180000
            },
            "MACOS": {
                "total_ms": 240000
            },
            "WINDOWS": {
                "total_ms": 300000
            }
        }
    }
}
```