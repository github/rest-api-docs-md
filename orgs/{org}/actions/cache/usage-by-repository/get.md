# List repositories with GitHub Actions cache usage for an organization

Lists repositories and their GitHub Actions cache usage for an organization.
The data fetched using this API is refreshed approximately every 5 minutes, so values returned from this endpoint may take at least 5 minutes to get updated.

OAuth tokens and personal access tokens (classic) need the `read:org` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "List repositories with GitHub Actions cache usage for an organization",
    "description": "Lists repositories and their GitHub Actions cache usage for an organization.\nThe data fetched using this API is refreshed approximately every 5 minutes, so values returned from this endpoint may take at least 5 minutes to get updated.\n\nOAuth tokens and personal access tokens (classic) need the `read:org` scope to use this endpoint.",
    "tags": [
        "actions"
    ],
    "operationId": "actions/get-actions-cache-usage-by-repo-for-org",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/actions/cache#list-repositories-with-github-actions-cache-usage-for-an-organization"
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
                            "repository_cache_usages"
                        ],
                        "properties": {
                            "total_count": {
                                "type": "integer"
                            },
                            "repository_cache_usages": {
                                "type": "array",
                                "items": {
                                    "$ref": "#/components/schemas/actions-cache-usage-by-repository"
                                }
                            }
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/org-actions-cache-usage-by-repo"
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
        "subcategory": "cache"
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

### `#/components/schemas/actions-cache-usage-by-repository`

```json
{
    "title": "Actions Cache Usage by repository",
    "description": "GitHub Actions Cache Usage by repository.",
    "type": "object",
    "properties": {
        "full_name": {
            "description": "The repository owner and name for the cache usage being shown.",
            "type": "string",
            "example": "octo-org/Hello-World"
        },
        "active_caches_size_in_bytes": {
            "description": "The sum of the size in bytes of all the active cache items in the repository.",
            "type": "integer",
            "example": 2322142
        },
        "active_caches_count": {
            "description": "The number of active caches in the repository.",
            "type": "integer",
            "example": 3
        }
    },
    "required": [
        "full_name",
        "active_caches_size_in_bytes",
        "active_caches_count"
    ]
}
```

### `#/components/examples/org-actions-cache-usage-by-repo`

```json
{
    "value": {
        "total_count": 2,
        "repository_cache_usages": [
            {
                "full_name": "octo-org/Hello-World",
                "active_caches_size_in_bytes": 2322142,
                "active_caches_count": 3
            },
            {
                "full_name": "octo-org/server",
                "active_caches_size_in_bytes": 1022142,
                "active_caches_count": 2
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