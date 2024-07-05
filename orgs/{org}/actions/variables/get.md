# List organization variables

Lists all organization variables.

Authenticated users must have collaborator access to a repository to create, update, or read variables.

OAuth app tokens and personal access tokens (classic) need the `admin:org` scope to use this endpoint. If the repository is private, the `repo` scope is also required.

## Operation Object

```json
{
    "summary": "List organization variables",
    "description": "Lists all organization variables.\n\nAuthenticated users must have collaborator access to a repository to create, update, or read variables.\n\nOAuth app tokens and personal access tokens (classic) need the `admin:org` scope to use this endpoint. If the repository is private, the `repo` scope is also required.",
    "tags": [
        "actions"
    ],
    "operationId": "actions/list-org-variables",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/actions/variables#list-organization-variables"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/org"
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
                                    "$ref": "#/components/schemas/organization-actions-variable"
                                }
                            }
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/organization-actions-variables-paginated"
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

### `#/components/schemas/organization-actions-variable`

```json
{
    "title": "Actions Variable for an Organization",
    "description": "Organization variable for GitHub Actions.",
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
            "example": "2019-01-24T22:45:36.000Z",
            "type": "string",
            "format": "date-time"
        },
        "updated_at": {
            "description": "The date and time at which the variable was last updated, in ISO 8601 format':' YYYY-MM-DDTHH:MM:SSZ.",
            "example": "2019-01-24T22:45:36.000Z",
            "type": "string",
            "format": "date-time"
        },
        "visibility": {
            "description": "Visibility of a variable",
            "enum": [
                "all",
                "private",
                "selected"
            ],
            "type": "string"
        },
        "selected_repositories_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/organizations/org/variables/USERNAME/repositories"
        }
    },
    "required": [
        "name",
        "value",
        "created_at",
        "updated_at",
        "visibility"
    ]
}
```

### `#/components/examples/organization-actions-variables-paginated`

```json
{
    "value": {
        "total_count": 3,
        "variables": [
            {
                "name": "USERNAME",
                "value": "octocat",
                "created_at": "2019-08-10T14:59:22Z",
                "updated_at": "2020-01-10T14:59:22Z",
                "visibility": "private"
            },
            {
                "name": "ACTIONS_RUNNER_DEBUG",
                "value": true,
                "created_at": "2019-08-10T14:59:22Z",
                "updated_at": "2020-01-10T14:59:22Z",
                "visibility": "all"
            },
            {
                "name": "ADMIN_EMAIL",
                "value": "octocat@github.com",
                "created_at": "2019-08-10T14:59:22Z",
                "updated_at": "2020-01-10T14:59:22Z",
                "visibility": "selected",
                "selected_repositories_url": "https://api.github.com/orgs/octo-org/actions/variables/ADMIN_EMAIL/repositories"
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