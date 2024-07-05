# List secrets for the authenticated user

`get /user/codespaces/secrets`

Lists all development environment secrets available for a user's codespaces without revealing their
encrypted values.

The authenticated user must have Codespaces access to use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `codespace` or `codespace:secrets` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "List secrets for the authenticated user",
    "description": "Lists all development environment secrets available for a user's codespaces without revealing their\nencrypted values.\n\nThe authenticated user must have Codespaces access to use this endpoint.\n\nOAuth app tokens and personal access tokens (classic) need the `codespace` or `codespace:secrets` scope to use this endpoint.",
    "tags": [
        "codespaces"
    ],
    "operationId": "codespaces/list-secrets-for-authenticated-user",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/codespaces/secrets#list-secrets-for-the-authenticated-user"
    },
    "parameters": [
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
                            "secrets"
                        ],
                        "properties": {
                            "total_count": {
                                "type": "integer"
                            },
                            "secrets": {
                                "type": "array",
                                "items": {
                                    "$ref": "#/components/schemas/codespaces-secret"
                                }
                            }
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/repo-codespaces-secret-paginated"
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
        "enabledForGitHubApps": false,
        "category": "codespaces",
        "subcategory": "secrets"
    }
}
```

## References

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

### `#/components/schemas/codespaces-secret`

```json
{
    "title": "Codespaces Secret",
    "description": "Secrets for a GitHub Codespace.",
    "type": "object",
    "properties": {
        "name": {
            "description": "The name of the secret",
            "example": "SECRET_NAME",
            "type": "string"
        },
        "created_at": {
            "description": "The date and time at which the secret was created, in ISO 8601 format':' YYYY-MM-DDTHH:MM:SSZ.",
            "type": "string",
            "format": "date-time"
        },
        "updated_at": {
            "description": "The date and time at which the secret was last updated, in ISO 8601 format':' YYYY-MM-DDTHH:MM:SSZ.",
            "type": "string",
            "format": "date-time"
        },
        "visibility": {
            "description": "The type of repositories in the organization that the secret is visible to",
            "enum": [
                "all",
                "private",
                "selected"
            ],
            "type": "string"
        },
        "selected_repositories_url": {
            "description": "The API URL at which the list of repositories this secret is visible to can be retrieved",
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/user/secrets/SECRET_NAME/repositories"
        }
    },
    "required": [
        "name",
        "created_at",
        "updated_at",
        "visibility",
        "selected_repositories_url"
    ]
}
```

### `#/components/examples/repo-codespaces-secret-paginated`

```json
{
    "value": {
        "total_count": 2,
        "secrets": [
            {
                "name": "GH_TOKEN",
                "created_at": "2019-08-10T14:59:22Z",
                "updated_at": "2020-01-10T14:59:22Z",
                "visibility": "all"
            },
            {
                "name": "GIST_ID",
                "created_at": "2020-01-10T10:59:22Z",
                "updated_at": "2020-01-11T11:59:22Z",
                "visibility": "all"
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