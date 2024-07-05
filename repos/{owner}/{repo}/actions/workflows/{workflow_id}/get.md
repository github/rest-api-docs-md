# Get a workflow

`get /repos/{owner}/{repo}/actions/workflows/{workflow_id}`

Gets a specific workflow. You can replace `workflow_id` with the workflow
file name. For example, you could use `main.yaml`.

Anyone with read access to the repository can use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint with a private repository.

## Operation Object

```json
{
    "summary": "Get a workflow",
    "description": "Gets a specific workflow. You can replace `workflow_id` with the workflow\nfile name. For example, you could use `main.yaml`.\n\nAnyone with read access to the repository can use this endpoint.\n\nOAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint with a private repository.",
    "tags": [
        "actions"
    ],
    "operationId": "actions/get-workflow",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/actions/workflows#get-a-workflow"
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
                        "$ref": "#/components/schemas/workflow"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/workflow"
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

### `#/components/schemas/workflow`

```json
{
    "title": "Workflow",
    "description": "A GitHub Actions workflow",
    "type": "object",
    "properties": {
        "id": {
            "type": "integer",
            "example": 5
        },
        "node_id": {
            "type": "string",
            "example": "MDg6V29ya2Zsb3cxMg=="
        },
        "name": {
            "type": "string",
            "example": "CI"
        },
        "path": {
            "type": "string",
            "example": "ruby.yaml"
        },
        "state": {
            "type": "string",
            "example": "active",
            "enum": [
                "active",
                "deleted",
                "disabled_fork",
                "disabled_inactivity",
                "disabled_manually"
            ]
        },
        "created_at": {
            "type": "string",
            "format": "date-time",
            "example": "2019-12-06T14:20:20.000Z"
        },
        "updated_at": {
            "type": "string",
            "format": "date-time",
            "example": "2019-12-06T14:20:20.000Z"
        },
        "url": {
            "type": "string",
            "example": "https://api.github.com/repos/actions/setup-ruby/workflows/5"
        },
        "html_url": {
            "type": "string",
            "example": "https://github.com/actions/setup-ruby/blob/master/.github/workflows/ruby.yaml"
        },
        "badge_url": {
            "type": "string",
            "example": "https://github.com/actions/setup-ruby/workflows/CI/badge.svg"
        },
        "deleted_at": {
            "type": "string",
            "format": "date-time",
            "example": "2019-12-06T14:20:20.000Z"
        }
    },
    "required": [
        "id",
        "node_id",
        "name",
        "path",
        "state",
        "url",
        "html_url",
        "badge_url",
        "created_at",
        "updated_at"
    ]
}
```

### `#/components/examples/workflow`

```json
{
    "value": {
        "id": 161335,
        "node_id": "MDg6V29ya2Zsb3cxNjEzMzU=",
        "name": "CI",
        "path": ".github/workflows/blank.yaml",
        "state": "active",
        "created_at": "2020-01-08T23:48:37.000-08:00",
        "updated_at": "2020-01-08T23:50:21.000-08:00",
        "url": "https://api.github.com/repos/octo-org/octo-repo/actions/workflows/161335",
        "html_url": "https://github.com/octo-org/octo-repo/blob/master/.github/workflows/161335",
        "badge_url": "https://github.com/octo-org/octo-repo/workflows/CI/badge.svg"
    }
}
```