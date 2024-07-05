# List repository variables

`get /repos/{owner}/{repo}/actions/variables`

Lists all repository variables.

Authenticated users must have collaborator access to a repository to create, update, or read variables.

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "List repository variables",
    "description": "Lists all repository variables.\n\nAuthenticated users must have collaborator access to a repository to create, update, or read variables.\n\nOAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.",
    "tags": [
        "actions"
    ],
    "operationId": "actions/list-repo-variables",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/actions/variables#list-repository-variables"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "$ref": "#/components/parameters/variables-per-page"
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
                            "variables"
                        ],
                        "properties": {
                            "total_count": {
                                "type": "integer"
                            },
                            "variables": {
                                "type": "array",
                                "items": {
                                    "$ref": "#/components/schemas/actions-variable"
                                }
                            }
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/actions-variables-paginated"
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
        "subcategory": "variables"
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

### `#/components/parameters/variables-per-page`

```json
{
    "name": "per_page",
    "description": "The number of results per page (max 30). For more information, see \"[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api).\"",
    "in": "query",
    "schema": {
        "type": "integer",
        "default": 10
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

### `#/components/schemas/actions-variable`

```json
{
    "title": "Actions Variable",
    "type": "object",
    "properties": {
        "name": {
            "description": "The name of the variable.",
            "example": "USERNAME",
            "type": "string"
        },
        "value": {
            "description": "The value of the variable.",
            "example": "octocat",
            "type": "string"
        },
        "created_at": {
            "description": "The date and time at which the variable was created, in ISO 8601 format':' YYYY-MM-DDTHH:MM:SSZ.",
            "type": "string",
            "format": "date-time",
            "example": "2019-01-24T22:45:36.000Z"
        },
        "updated_at": {
            "description": "The date and time at which the variable was last updated, in ISO 8601 format':' YYYY-MM-DDTHH:MM:SSZ.",
            "type": "string",
            "format": "date-time",
            "example": "2019-01-24T22:45:36.000Z"
        }
    },
    "required": [
        "name",
        "value",
        "created_at",
        "updated_at"
    ]
}
```

### `#/components/examples/actions-variables-paginated`

```json
{
    "value": {
        "total_count": 2,
        "variables": [
            {
                "name": "USERNAME",
                "value": "octocat",
                "created_at": "2019-08-10T14:59:22Z",
                "updated_at": "2020-01-10T14:59:22Z"
            },
            {
                "name": "EMAIL",
                "value": "octocat@github.com",
                "created_at": "2020-01-10T10:59:22Z",
                "updated_at": "2020-01-11T11:59:22Z"
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