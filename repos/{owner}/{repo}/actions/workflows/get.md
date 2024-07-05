# List repository workflows

`get /repos/{owner}/{repo}/actions/workflows`

Lists the workflows in a repository.

Anyone with read access to the repository can use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint with a private repository.

## Operation Object

```json
{
    "summary": "List repository workflows",
    "description": "Lists the workflows in a repository.\n\nAnyone with read access to the repository can use this endpoint.\n\nOAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint with a private repository.",
    "tags": [
        "actions"
    ],
    "operationId": "actions/list-repo-workflows",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/actions/workflows#list-repository-workflows"
    },
    "parameters": [
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
                            "workflows"
                        ],
                        "properties": {
                            "total_count": {
                                "type": "integer"
                            },
                            "workflows": {
                                "type": "array",
                                "items": {
                                    "$ref": "#/components/schemas/workflow"
                                }
                            }
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/workflow-paginated"
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

### `#/components/examples/workflow-paginated`

```json
{
    "value": {
        "total_count": 2,
        "workflows": [
            {
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
            },
            {
                "id": 269289,
                "node_id": "MDE4OldvcmtmbG93IFNlY29uZGFyeTI2OTI4OQ==",
                "name": "Linter",
                "path": ".github/workflows/linter.yaml",
                "state": "active",
                "created_at": "2020-01-08T23:48:37.000-08:00",
                "updated_at": "2020-01-08T23:50:21.000-08:00",
                "url": "https://api.github.com/repos/octo-org/octo-repo/actions/workflows/269289",
                "html_url": "https://github.com/octo-org/octo-repo/blob/master/.github/workflows/269289",
                "badge_url": "https://github.com/octo-org/octo-repo/workflows/Linter/badge.svg"
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