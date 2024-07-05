# Get page views

Get the total number of views and breakdown per day or week for the last 14 days. Timestamps are aligned to UTC midnight of the beginning of the day or week. Week begins on Monday.

## Operation Object

```json
{
    "summary": "Get page views",
    "description": "Get the total number of views and breakdown per day or week for the last 14 days. Timestamps are aligned to UTC midnight of the beginning of the day or week. Week begins on Monday.",
    "tags": [
        "repos"
    ],
    "operationId": "repos/get-views",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/metrics/traffic#get-page-views"
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
                        "$ref": "#/components/schemas/view-traffic"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/view-traffic"
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

### `#/components/schemas/view-traffic`

```json
{
    "title": "View Traffic",
    "description": "View Traffic",
    "type": "object",
    "properties": {
        "count": {
            "type": "integer",
            "example": 14850
        },
        "uniques": {
            "type": "integer",
            "example": 3782
        },
        "views": {
            "type": "array",
            "items": {
                "$ref": "#/components/schemas/traffic"
            }
        }
    },
    "required": [
        "uniques",
        "count",
        "views"
    ]
}
```

### `#/components/examples/view-traffic`

```json
{
    "value": {
        "count": 14850,
        "uniques": 3782,
        "views": [
            {
                "timestamp": "2016-10-10T00:00:00Z",
                "count": 440,
                "uniques": 143
            },
            {
                "timestamp": "2016-10-11T00:00:00Z",
                "count": 1308,
                "uniques": 414
            },
            {
                "timestamp": "2016-10-12T00:00:00Z",
                "count": 1486,
                "uniques": 452
            },
            {
                "timestamp": "2016-10-13T00:00:00Z",
                "count": 1170,
                "uniques": 401
            },
            {
                "timestamp": "2016-10-14T00:00:00Z",
                "count": 868,
                "uniques": 266
            },
            {
                "timestamp": "2016-10-15T00:00:00Z",
                "count": 495,
                "uniques": 157
            },
            {
                "timestamp": "2016-10-16T00:00:00Z",
                "count": 524,
                "uniques": 175
            },
            {
                "timestamp": "2016-10-17T00:00:00Z",
                "count": 1263,
                "uniques": 412
            },
            {
                "timestamp": "2016-10-18T00:00:00Z",
                "count": 1402,
                "uniques": 417
            },
            {
                "timestamp": "2016-10-19T00:00:00Z",
                "count": 1394,
                "uniques": 424
            },
            {
                "timestamp": "2016-10-20T00:00:00Z",
                "count": 1492,
                "uniques": 448
            },
            {
                "timestamp": "2016-10-21T00:00:00Z",
                "count": 1153,
                "uniques": 332
            },
            {
                "timestamp": "2016-10-22T00:00:00Z",
                "count": 566,
                "uniques": 168
            },
            {
                "timestamp": "2016-10-23T00:00:00Z",
                "count": 675,
                "uniques": 184
            },
            {
                "timestamp": "2016-10-24T00:00:00Z",
                "count": 614,
                "uniques": 237
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