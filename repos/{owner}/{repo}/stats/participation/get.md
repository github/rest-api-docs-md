# Get the weekly commit count

Returns the total commit counts for the `owner` and total commit counts in `all`. `all` is everyone combined, including the `owner` in the last 52 weeks. If you'd like to get the commit counts for non-owners, you can subtract `owner` from `all`.

The array order is oldest week (index 0) to most recent week.

The most recent week is seven days ago at UTC midnight to today at UTC midnight.

## Operation Object

```json
{
    "summary": "Get the weekly commit count",
    "description": "Returns the total commit counts for the `owner` and total commit counts in `all`. `all` is everyone combined, including the `owner` in the last 52 weeks. If you'd like to get the commit counts for non-owners, you can subtract `owner` from `all`.\n\nThe array order is oldest week (index 0) to most recent week.\n\nThe most recent week is seven days ago at UTC midnight to today at UTC midnight.",
    "tags": [
        "repos"
    ],
    "operationId": "repos/get-participation-stats",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/metrics/statistics#get-the-weekly-commit-count"
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
            "description": "The array order is oldest week (index 0) to most recent week.",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/participation-stats"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/participation-stats"
                        }
                    }
                }
            }
        },
        "404": {
            "$ref": "#/components/responses/not_found"
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

### `#/components/schemas/participation-stats`

```json
{
    "title": "Participation Stats",
    "type": "object",
    "properties": {
        "all": {
            "type": "array",
            "items": {
                "type": "integer"
            }
        },
        "owner": {
            "type": "array",
            "items": {
                "type": "integer"
            }
        }
    },
    "required": [
        "all",
        "owner"
    ]
}
```

### `#/components/examples/participation-stats`

```json
{
    "value": {
        "all": [
            11,
            21,
            15,
            2,
            8,
            1,
            8,
            23,
            17,
            21,
            11,
            10,
            33,
            91,
            38,
            34,
            22,
            23,
            32,
            3,
            43,
            87,
            71,
            18,
            13,
            5,
            13,
            16,
            66,
            27,
            12,
            45,
            110,
            117,
            13,
            8,
            18,
            9,
            19,
            26,
            39,
            12,
            20,
            31,
            46,
            91,
            45,
            10,
            24,
            9,
            29,
            7
        ],
        "owner": [
            3,
            2,
            3,
            0,
            2,
            0,
            5,
            14,
            7,
            9,
            1,
            5,
            0,
            48,
            19,
            2,
            0,
            1,
            10,
            2,
            23,
            40,
            35,
            8,
            8,
            2,
            10,
            6,
            30,
            0,
            2,
            9,
            53,
            104,
            3,
            3,
            10,
            4,
            7,
            11,
            21,
            4,
            4,
            22,
            26,
            63,
            11,
            2,
            14,
            1,
            10,
            3
        ]
    }
}
```

### `#/components/responses/not_found`

```json
{
    "description": "Resource not found",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/basic-error"
            }
        }
    }
}
```