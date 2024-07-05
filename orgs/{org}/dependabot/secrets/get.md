# List organization secrets

`get /orgs/{org}/dependabot/secrets`

Lists all secrets available in an organization without revealing their
encrypted values.

OAuth app tokens and personal access tokens (classic) need the `admin:org` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "List organization secrets",
    "description": "Lists all secrets available in an organization without revealing their\nencrypted values.\n\nOAuth app tokens and personal access tokens (classic) need the `admin:org` scope to use this endpoint.",
    "tags": [
        "dependabot"
    ],
    "operationId": "dependabot/list-org-secrets",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/dependabot/secrets#list-organization-secrets"
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
                                    "$ref": "#/components/schemas/organization-dependabot-secret"
                                }
                            }
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/organization-dependabot-secret-paginated"
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

### `#/components/schemas/organization-dependabot-secret`

```json
{
    "title": "Dependabot Secret for an Organization",
    "description": "Secrets for GitHub Dependabot for an organization.",
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
            "example": "https://api.github.com/organizations/org/dependabot/secrets/my_secret/repositories"
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

### `#/components/examples/organization-dependabot-secret-paginated`

```json
{
    "value": {
        "total_count": 3,
        "secrets": [
            {
                "name": "MY_ARTIFACTORY_PASSWORD",
                "created_at": "2021-08-10T14:59:22Z",
                "updated_at": "2021-12-10T14:59:22Z",
                "visibility": "private"
            },
            {
                "name": "NPM_TOKEN",
                "created_at": "2021-08-10T14:59:22Z",
                "updated_at": "2021-12-10T14:59:22Z",
                "visibility": "all"
            },
            {
                "name": "GH_TOKEN",
                "created_at": "2021-08-10T14:59:22Z",
                "updated_at": "2021-12-10T14:59:22Z",
                "visibility": "selected",
                "selected_repositories_url": "https://api.github.com/orgs/octo-org/dependabot/secrets/SUPER_SECRET/repositories"
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