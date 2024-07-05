# Get GitHub Actions cache usage for an organization

`get /orgs/{org}/actions/cache/usage`

Gets the total GitHub Actions cache usage for an organization.
The data fetched using this API is refreshed approximately every 5 minutes, so values returned from this endpoint may take at least 5 minutes to get updated.

OAuth tokens and personal access tokens (classic) need the `read:org` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "Get GitHub Actions cache usage for an organization",
    "description": "Gets the total GitHub Actions cache usage for an organization.\nThe data fetched using this API is refreshed approximately every 5 minutes, so values returned from this endpoint may take at least 5 minutes to get updated.\n\nOAuth tokens and personal access tokens (classic) need the `read:org` scope to use this endpoint.",
    "tags": [
        "actions"
    ],
    "operationId": "actions/get-actions-cache-usage-for-org",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/actions/cache#get-github-actions-cache-usage-for-an-organization"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/org"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/actions-cache-usage-org-enterprise"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/actions-cache-usage-org-enterprise"
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

### `#/components/schemas/actions-cache-usage-org-enterprise`

```json
{
    "type": "object",
    "properties": {
        "total_active_caches_count": {
            "type": "integer",
            "description": "The count of active caches across all repositories of an enterprise or an organization."
        },
        "total_active_caches_size_in_bytes": {
            "type": "integer",
            "description": "The total size in bytes of all active cache items across all repositories of an enterprise or an organization."
        }
    },
    "required": [
        "total_active_caches_count",
        "total_active_caches_size_in_bytes"
    ]
}
```

### `#/components/examples/actions-cache-usage-org-enterprise`

```json
{
    "value": {
        "total_active_caches_size_in_bytes": 3344284,
        "total_active_caches_count": 5
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