# List organization secrets

Lists all secrets available in an organization without revealing their
encrypted values.

Authenticated users must have collaborator access to a repository to create, update, or read secrets.

OAuth app tokens and personal access tokens (classic) need the `admin:org` scope to use this endpoint. If the repository is private, the `repo` scope is also required.

## Operation Object

```json
{
    "summary": "List organization secrets",
    "description": "Lists all secrets available in an organization without revealing their\nencrypted values.\n\nAuthenticated users must have collaborator access to a repository to create, update, or read secrets.\n\nOAuth app tokens and personal access tokens (classic) need the `admin:org` scope to use this endpoint. If the repository is private, the `repo` scope is also required.",
    "tags": [
        "actions"
    ],
    "operationId": "actions/list-org-secrets",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/actions/secrets#list-organization-secrets"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/org"
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
                                    "$ref": "#/components/schemas/organization-actions-secret"
                                }
                            }
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/organization-actions-secret-paginated"
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
        "subcategory": "secrets"
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

### `#/components/schemas/organization-actions-secret`

```json
{
    "title": "Actions Secret for an Organization",
    "description": "Secrets for GitHub Actions for an organization.",
    "type": "object",
    "properties": {
        "name": {
            "description": "The name of the secret.",
            "example": "SECRET_TOKEN",
            "type": "string"
        },
        "created_at": {
            "type": "string",
            "format": "date-time"
        },
        "updated_at": {
            "type": "string",
            "format": "date-time"
        },
        "visibility": {
            "description": "Visibility of a secret",
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
            "example": "https://api.github.com/organizations/org/secrets/my_secret/repositories"
        }
    },
    "required": [
        "name",
        "created_at",
        "updated_at",
        "visibility"
    ]
}
```

### `#/components/examples/organization-actions-secret-paginated`

```json
{
    "value": {
        "total_count": 3,
        "secrets": [
            {
                "name": "GIST_ID",
                "created_at": "2019-08-10T14:59:22Z",
                "updated_at": "2020-01-10T14:59:22Z",
                "visibility": "private"
            },
            {
                "name": "DEPLOY_TOKEN",
                "created_at": "2019-08-10T14:59:22Z",
                "updated_at": "2020-01-10T14:59:22Z",
                "visibility": "all"
            },
            {
                "name": "GH_TOKEN",
                "created_at": "2019-08-10T14:59:22Z",
                "updated_at": "2020-01-10T14:59:22Z",
                "visibility": "selected",
                "selected_repositories_url": "https://api.github.com/orgs/octo-org/actions/secrets/SUPER_SECRET/repositories"
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