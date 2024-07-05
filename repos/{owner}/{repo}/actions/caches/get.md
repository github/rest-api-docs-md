# List GitHub Actions caches for a repository

Lists the GitHub Actions caches for a repository.

OAuth tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "List GitHub Actions caches for a repository",
    "description": "Lists the GitHub Actions caches for a repository.\n\nOAuth tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.",
    "tags": [
        "actions"
    ],
    "operationId": "actions/get-actions-cache-list",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/actions/cache#list-github-actions-caches-for-a-repository"
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
        },
        {
            "$ref": "#/components/parameters/actions-cache-git-ref-full"
        },
        {
            "$ref": "#/components/parameters/actions-cache-key"
        },
        {
            "$ref": "#/components/parameters/actions-cache-list-sort"
        },
        {
            "$ref": "#/components/parameters/direction"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/actions-cache-list"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/actions-cache-list"
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
        "previews": [],
        "category": "actions",
        "subcategory": "cache"
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

### `#/components/parameters/actions-cache-git-ref-full`

```json
{
    "name": "ref",
    "description": "The full Git reference for narrowing down the cache. The `ref` for a branch should be formatted as `refs/heads/<branch name>`. To reference a pull request use `refs/pull/<number>/merge`.",
    "in": "query",
    "required": false,
    "schema": {
        "type": "string"
    }
}
```

### `#/components/parameters/actions-cache-key`

```json
{
    "name": "key",
    "description": "An explicit key or prefix for identifying the cache",
    "in": "query",
    "required": false,
    "schema": {
        "type": "string"
    }
}
```

### `#/components/parameters/actions-cache-list-sort`

```json
{
    "name": "sort",
    "description": "The property to sort the results by. `created_at` means when the cache was created. `last_accessed_at` means when the cache was last accessed. `size_in_bytes` is the size of the cache in bytes.",
    "in": "query",
    "required": false,
    "schema": {
        "type": "string",
        "enum": [
            "created_at",
            "last_accessed_at",
            "size_in_bytes"
        ],
        "default": "last_accessed_at"
    }
}
```

### `#/components/parameters/direction`

```json
{
    "name": "direction",
    "description": "The direction to sort the results by.",
    "in": "query",
    "required": false,
    "schema": {
        "type": "string",
        "enum": [
            "asc",
            "desc"
        ],
        "default": "desc"
    }
}
```

### `#/components/schemas/actions-cache-list`

```json
{
    "title": "Repository actions caches",
    "description": "Repository actions caches",
    "type": "object",
    "properties": {
        "total_count": {
            "description": "Total number of caches",
            "type": "integer",
            "example": 2
        },
        "actions_caches": {
            "description": "Array of caches",
            "type": "array",
            "items": {
                "type": "object",
                "properties": {
                    "id": {
                        "type": "integer",
                        "example": 2
                    },
                    "ref": {
                        "type": "string",
                        "example": "refs/heads/main"
                    },
                    "key": {
                        "type": "string",
                        "example": "Linux-node-958aff96db2d75d67787d1e634ae70b659de937b"
                    },
                    "version": {
                        "type": "string",
                        "example": "73885106f58cc52a7df9ec4d4a5622a5614813162cb516c759a30af6bf56e6f0"
                    },
                    "last_accessed_at": {
                        "type": "string",
                        "format": "date-time",
                        "example": "2019-01-24T22:45:36.000Z"
                    },
                    "created_at": {
                        "type": "string",
                        "format": "date-time",
                        "example": "2019-01-24T22:45:36.000Z"
                    },
                    "size_in_bytes": {
                        "type": "integer",
                        "example": 1024
                    }
                }
            }
        }
    },
    "required": [
        "total_count",
        "actions_caches"
    ]
}
```

### `#/components/examples/actions-cache-list`

```json
{
    "value": {
        "total_count": 1,
        "actions_caches": [
            {
                "id": 505,
                "ref": "refs/heads/main",
                "key": "Linux-node-958aff96db2d75d67787d1e634ae70b659de937b",
                "version": "73885106f58cc52a7df9ec4d4a5622a5614813162cb516c759a30af6bf56e6f0",
                "last_accessed_at": "2019-01-24T22:45:36.000Z",
                "created_at": "2019-01-24T22:45:36.000Z",
                "size_in_bytes": 1024
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