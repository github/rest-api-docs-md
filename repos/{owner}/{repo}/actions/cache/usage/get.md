# Get GitHub Actions cache usage for a repository

`get /repos/{owner}/{repo}/actions/cache/usage`

Gets GitHub Actions cache usage for a repository.
The data fetched using this API is refreshed approximately every 5 minutes, so values returned from this endpoint may take at least 5 minutes to get updated.

Anyone with read access to the repository can use this endpoint.

If the repository is private, OAuth tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "Get GitHub Actions cache usage for a repository",
    "description": "Gets GitHub Actions cache usage for a repository.\nThe data fetched using this API is refreshed approximately every 5 minutes, so values returned from this endpoint may take at least 5 minutes to get updated.\n\nAnyone with read access to the repository can use this endpoint.\n\nIf the repository is private, OAuth tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.",
    "tags": [
        "actions"
    ],
    "operationId": "actions/get-actions-cache-usage",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/actions/cache#get-github-actions-cache-usage-for-a-repository"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/actions-cache-usage-by-repository"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/actions-cache-usage"
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

### `#/components/examples/actions-cache-usage`

```json
{
    "value": {
        "full_name": "octo-org/Hello-World",
        "active_caches_size_in_bytes": 2322142,
        "active_caches_count": 3
    }
}
```