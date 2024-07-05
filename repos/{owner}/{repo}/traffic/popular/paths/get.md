# Get top referral paths

`get /repos/{owner}/{repo}/traffic/popular/paths`

Get the top 10 popular contents over the last 14 days.

## Operation Object

```json
{
    "summary": "Get top referral paths",
    "description": "Get the top 10 popular contents over the last 14 days.",
    "tags": [
        "repos"
    ],
    "operationId": "repos/get-top-paths",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/metrics/traffic#get-top-referral-paths"
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
                            "$ref": "#/components/schemas/content-traffic"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/content-traffic-items"
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

### `#/components/schemas/content-traffic`

```json
{
    "title": "Content Traffic",
    "description": "Content Traffic",
    "type": "object",
    "properties": {
        "path": {
            "type": "string",
            "example": "/github/hubot"
        },
        "title": {
            "type": "string",
            "example": "github/hubot: A customizable life embetterment robot."
        },
        "count": {
            "type": "integer",
            "example": 3542
        },
        "uniques": {
            "type": "integer",
            "example": 2225
        }
    },
    "required": [
        "path",
        "title",
        "uniques",
        "count"
    ]
}
```

### `#/components/examples/content-traffic-items`

```json
{
    "value": [
        {
            "path": "/github/hubot",
            "title": "github/hubot: A customizable life embetterment robot.",
            "count": 3542,
            "uniques": 2225
        },
        {
            "path": "/github/hubot/blob/master/docs/scripting.md",
            "title": "hubot/scripting.md at master \u00b7 github/hubot \u00b7 GitHub",
            "count": 1707,
            "uniques": 804
        },
        {
            "path": "/github/hubot/tree/master/docs",
            "title": "hubot/docs at master \u00b7 github/hubot \u00b7 GitHub",
            "count": 685,
            "uniques": 435
        },
        {
            "path": "/github/hubot/tree/master/src",
            "title": "hubot/src at master \u00b7 github/hubot \u00b7 GitHub",
            "count": 577,
            "uniques": 347
        },
        {
            "path": "/github/hubot/blob/master/docs/index.md",
            "title": "hubot/index.md at master \u00b7 github/hubot \u00b7 GitHub",
            "count": 379,
            "uniques": 259
        },
        {
            "path": "/github/hubot/blob/master/docs/adapters.md",
            "title": "hubot/adapters.md at master \u00b7 github/hubot \u00b7 GitHub",
            "count": 354,
            "uniques": 201
        },
        {
            "path": "/github/hubot/tree/master/examples",
            "title": "hubot/examples at master \u00b7 github/hubot \u00b7 GitHub",
            "count": 340,
            "uniques": 260
        },
        {
            "path": "/github/hubot/blob/master/docs/deploying/heroku.md",
            "title": "hubot/heroku.md at master \u00b7 github/hubot \u00b7 GitHub",
            "count": 324,
            "uniques": 217
        },
        {
            "path": "/github/hubot/blob/master/src/robot.coffee",
            "title": "hubot/robot.coffee at master \u00b7 github/hubot \u00b7 GitHub",
            "count": 293,
            "uniques": 191
        },
        {
            "path": "/github/hubot/blob/master/LICENSE.md",
            "title": "hubot/LICENSE.md at master \u00b7 github/hubot \u00b7 GitHub",
            "count": 281,
            "uniques": 222
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