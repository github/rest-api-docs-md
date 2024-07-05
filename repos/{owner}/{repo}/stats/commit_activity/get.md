# Get the last year of commit activity

`get /repos/{owner}/{repo}/stats/commit_activity`

Returns the last year of commit activity grouped by week. The `days` array is a group of commits per day, starting on `Sunday`.

## Operation Object

```json
{
    "summary": "Get the last year of commit activity",
    "description": "Returns the last year of commit activity grouped by week. The `days` array is a group of commits per day, starting on `Sunday`.",
    "tags": [
        "repos"
    ],
    "operationId": "repos/get-commit-activity-stats",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/metrics/statistics#get-the-last-year-of-commit-activity"
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
                        "type": "array",
                        "items": {
                            "$ref": "#/components/schemas/commit-activity"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/commit-activity-items"
                        }
                    }
                }
            }
        },
        "202": {
            "$ref": "#/components/responses/accepted"
        },
        "204": {
            "$ref": "#/components/responses/no_content"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "metrics",
        "subcategory": "statistics"
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

### `#/components/schemas/commit-activity`

```json
{
    "title": "Commit Activity",
    "description": "Commit Activity",
    "type": "object",
    "properties": {
        "days": {
            "type": "array",
            "example": [
                0,
                3,
                26,
                20,
                39,
                1,
                0
            ],
            "items": {
                "type": "integer"
            }
        },
        "total": {
            "type": "integer",
            "example": 89
        },
        "week": {
            "type": "integer",
            "example": 1336280400
        }
    },
    "required": [
        "days",
        "total",
        "week"
    ]
}
```

### `#/components/examples/commit-activity-items`

```json
{
    "value": [
        {
            "days": [
                0,
                3,
                26,
                20,
                39,
                1,
                0
            ],
            "total": 89,
            "week": 1336280400
        }
    ]
}
```

### `#/components/responses/accepted`

```json
{
    "description": "Accepted",
    "content": {
        "application/json": {
            "schema": {
                "type": "object"
            },
            "examples": {
                "default": {
                    "value": null
                }
            }
        }
    }
}
```

### `#/components/responses/no_content`

```json
{
    "description": "A header with no content is returned."
}
```