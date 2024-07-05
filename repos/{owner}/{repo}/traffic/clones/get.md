# Get repository clones

Get the total number of clones and breakdown per day or week for the last 14 days. Timestamps are aligned to UTC midnight of the beginning of the day or week. Week begins on Monday.

## Operation Object

```json
{
    "summary": "Get repository clones",
    "description": "Get the total number of clones and breakdown per day or week for the last 14 days. Timestamps are aligned to UTC midnight of the beginning of the day or week. Week begins on Monday.",
    "tags": [
        "repos"
    ],
    "operationId": "repos/get-clones",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/metrics/traffic#get-repository-clones"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "$ref": "#/components/parameters/per"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/clone-traffic"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/clone-traffic"
                        }
                    }
                }
            }
        },
        "403": {
            "$ref": "#/components/responses/forbidden"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "metrics",
        "subcategory": "traffic"
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

### `#/components/parameters/per`

```json
{
    "name": "per",
    "description": "The time frame to display results for.",
    "in": "query",
    "required": false,
    "schema": {
        "type": "string",
        "enum": [
            "day",
            "week"
        ],
        "default": "day"
    }
}
```

### `#/components/schemas/clone-traffic`

```json
{
    "title": "Clone Traffic",
    "description": "Clone Traffic",
    "type": "object",
    "properties": {
        "count": {
            "type": "integer",
            "example": 173
        },
        "uniques": {
            "type": "integer",
            "example": 128
        },
        "clones": {
            "type": "array",
            "items": {
                "$ref": "#/components/schemas/traffic"
            }
        }
    },
    "required": [
        "uniques",
        "count",
        "clones"
    ]
}
```

### `#/components/examples/clone-traffic`

```json
{
    "value": {
        "count": 173,
        "uniques": 128,
        "clones": [
            {
                "timestamp": "2016-10-10T00:00:00Z",
                "count": 2,
                "uniques": 1
            },
            {
                "timestamp": "2016-10-11T00:00:00Z",
                "count": 17,
                "uniques": 16
            },
            {
                "timestamp": "2016-10-12T00:00:00Z",
                "count": 21,
                "uniques": 15
            },
            {
                "timestamp": "2016-10-13T00:00:00Z",
                "count": 8,
                "uniques": 7
            },
            {
                "timestamp": "2016-10-14T00:00:00Z",
                "count": 5,
                "uniques": 5
            },
            {
                "timestamp": "2016-10-15T00:00:00Z",
                "count": 2,
                "uniques": 2
            },
            {
                "timestamp": "2016-10-16T00:00:00Z",
                "count": 8,
                "uniques": 7
            },
            {
                "timestamp": "2016-10-17T00:00:00Z",
                "count": 26,
                "uniques": 15
            },
            {
                "timestamp": "2016-10-18T00:00:00Z",
                "count": 19,
                "uniques": 17
            },
            {
                "timestamp": "2016-10-19T00:00:00Z",
                "count": 19,
                "uniques": 14
            },
            {
                "timestamp": "2016-10-20T00:00:00Z",
                "count": 19,
                "uniques": 15
            },
            {
                "timestamp": "2016-10-21T00:00:00Z",
                "count": 9,
                "uniques": 7
            },
            {
                "timestamp": "2016-10-22T00:00:00Z",
                "count": 5,
                "uniques": 5
            },
            {
                "timestamp": "2016-10-23T00:00:00Z",
                "count": 6,
                "uniques": 5
            },
            {
                "timestamp": "2016-10-24T00:00:00Z",
                "count": 7,
                "uniques": 5
            }
        ]
    }
}
```

### `#/components/responses/forbidden`

```json
{
    "description": "Forbidden",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/basic-error"
            }
        }
    }
}
```