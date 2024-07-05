# Get the weekly commit activity

`get /repos/{owner}/{repo}/stats/code_frequency`


Returns a weekly aggregate of the number of additions and deletions pushed to a repository.

**Note:** This endpoint can only be used for repositories with fewer than 10,000 commits. If the repository contains
10,000 or more commits, a 422 status code will be returned.


## Operation Object

```json
{
    "summary": "Get the weekly commit activity",
    "description": "\nReturns a weekly aggregate of the number of additions and deletions pushed to a repository.\n\n**Note:** This endpoint can only be used for repositories with fewer than 10,000 commits. If the repository contains\n10,000 or more commits, a 422 status code will be returned.\n",
    "tags": [
        "repos"
    ],
    "operationId": "repos/get-code-frequency-stats",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/metrics/statistics#get-the-weekly-commit-activity"
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
            "description": "Returns a weekly aggregate of the number of additions and deletions pushed to a repository.",
            "content": {
                "application/json": {
                    "schema": {
                        "type": "array",
                        "items": {
                            "$ref": "#/components/schemas/code-frequency-stat"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/code-frequency-stat-items"
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
        },
        "422": {
            "description": "Repository contains more than 10,000 commits"
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

### `#/components/schemas/code-frequency-stat`

```json
{
    "title": "Code Frequency Stat",
    "description": "Code Frequency Stat",
    "type": "array",
    "items": {
        "type": "integer"
    }
}
```

### `#/components/examples/code-frequency-stat-items`

```json
{
    "value": [
        [
            1302998400,
            1124,
            -435
        ]
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