# Get top referral sources

Get the top 10 referrers over the last 14 days.

## Operation Object

```json
{
    "summary": "Get top referral sources",
    "description": "Get the top 10 referrers over the last 14 days.",
    "tags": [
        "repos"
    ],
    "operationId": "repos/get-top-referrers",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/metrics/traffic#get-top-referral-sources"
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
                            "$ref": "#/components/schemas/referrer-traffic"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/referrer-traffic-items"
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

### `#/components/schemas/referrer-traffic`

```json
{
    "title": "Referrer Traffic",
    "description": "Referrer Traffic",
    "type": "object",
    "properties": {
        "referrer": {
            "type": "string",
            "example": "Google"
        },
        "count": {
            "type": "integer",
            "example": 4
        },
        "uniques": {
            "type": "integer",
            "example": 3
        }
    },
    "required": [
        "referrer",
        "uniques",
        "count"
    ]
}
```

### `#/components/examples/referrer-traffic-items`

```json
{
    "value": [
        {
            "referrer": "Google",
            "count": 4,
            "uniques": 3
        },
        {
            "referrer": "stackoverflow.com",
            "count": 2,
            "uniques": 2
        },
        {
            "referrer": "eggsonbread.com",
            "count": 1,
            "uniques": 1
        },
        {
            "referrer": "yandex.ru",
            "count": 1,
            "uniques": 1
        }
    ]
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