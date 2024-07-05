# List repository secrets

Lists all secrets available in a repository without revealing their encrypted
values.

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "List repository secrets",
    "description": "Lists all secrets available in a repository without revealing their encrypted\nvalues.\n\nOAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.",
    "tags": [
        "dependabot"
    ],
    "operationId": "dependabot/list-repo-secrets",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/dependabot/secrets#list-repository-secrets"
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
                            "secrets"
                        ],
                        "properties": {
                            "total_count": {
                                "type": "integer"
                            },
                            "secrets": {
                                "type": "array",
                                "items": {
                                    "$ref": "#/components/schemas/dependabot-secret"
                                }
                            }
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/dependabot-secret-paginated"
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
        "category": "dependabot",
        "subcategory": "secrets"
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

### `#/components/schemas/dependabot-secret`

```json
{
    "title": "Dependabot Secret",
    "description": "Set secrets for Dependabot.",
    "type": "object",
    "properties": {
        "name": {
            "description": "The name of the secret.",
            "example": "MY_ARTIFACTORY_PASSWORD",
            "type": "string"
        },
        "created_at": {
            "type": "string",
            "format": "date-time"
        },
        "updated_at": {
            "type": "string",
            "format": "date-time"
        }
    },
    "required": [
        "name",
        "created_at",
        "updated_at"
    ]
}
```

### `#/components/examples/dependabot-secret-paginated`

```json
{
    "value": {
        "total_count": 2,
        "secrets": [
            {
                "name": "AZURE_DEVOPS_PAT",
                "created_at": "2019-08-10T14:59:22Z",
                "updated_at": "2020-01-10T14:59:22Z"
            },
            {
                "name": "MY_ARTIFACTORY_PASSWORD",
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