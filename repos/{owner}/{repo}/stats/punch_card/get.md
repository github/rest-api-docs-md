# Get the hourly commit count for each day

Each array contains the day number, hour number, and number of commits:

*   `0-6`: Sunday - Saturday
*   `0-23`: Hour of day
*   Number of commits

For example, `[2, 14, 25]` indicates that there were 25 total commits, during the 2:00pm hour on Tuesdays. All times are based on the time zone of individual commits.

## Operation Object

```json
{
    "summary": "Get the hourly commit count for each day",
    "description": "Each array contains the day number, hour number, and number of commits:\n\n*   `0-6`: Sunday - Saturday\n*   `0-23`: Hour of day\n*   Number of commits\n\nFor example, `[2, 14, 25]` indicates that there were 25 total commits, during the 2:00pm hour on Tuesdays. All times are based on the time zone of individual commits.",
    "tags": [
        "repos"
    ],
    "operationId": "repos/get-punch-card-stats",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/metrics/statistics#get-the-hourly-commit-count-for-each-day"
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
            "description": "For example, `[2, 14, 25]` indicates that there were 25 total commits, during the 2:00pm hour on Tuesdays. All times are based on the time zone of individual commits.",
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
                            "$ref": "#/components/examples/code-frequency-stat-items-2"
                        }
                    }
                }
            }
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

### `#/components/examples/code-frequency-stat-items-2`

```json
{
    "value": [
        [
            0,
            0,
            5
        ],
        [
            0,
            1,
            43
        ],
        [
            0,
            2,
            21
        ]
    ]
}
```

### `#/components/responses/no_content`

```json
{
    "description": "A header with no content is returned."
}
```