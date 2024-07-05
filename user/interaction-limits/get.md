# Get interaction restrictions for your public repositories

`get /user/interaction-limits`

Shows which type of GitHub user can interact with your public repositories and when the restriction expires.

## Operation Object

```json
{
    "summary": "Get interaction restrictions for your public repositories",
    "description": "Shows which type of GitHub user can interact with your public repositories and when the restriction expires.",
    "tags": [
        "interactions"
    ],
    "operationId": "interactions/get-restrictions-for-authenticated-user",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/interactions/user#get-interaction-restrictions-for-your-public-repositories"
    },
    "responses": {
        "200": {
            "description": "Default response",
            "content": {
                "application/json": {
                    "schema": {
                        "anyOf": [
                            {
                                "$ref": "#/components/schemas/interaction-limit-response"
                            },
                            {
                                "type": "object",
                                "properties": {},
                                "additionalProperties": false
                            }
                        ]
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/interaction-limit-response"
                        }
                    }
                }
            }
        },
        "204": {
            "description": "Response when there are no restrictions"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": false,
        "category": "interactions",
        "subcategory": "user"
    }
}
```

## References

### `#/components/schemas/interaction-limit-response`

```json
{
    "title": "Interaction Limits",
    "description": "Interaction limit settings.",
    "type": "object",
    "properties": {
        "limit": {
            "$ref": "#/components/schemas/interaction-group"
        },
        "origin": {
            "type": "string",
            "example": "repository"
        },
        "expires_at": {
            "type": "string",
            "format": "date-time",
            "example": "2018-08-17T04:18:39Z"
        }
    },
    "required": [
        "limit",
        "origin",
        "expires_at"
    ]
}
```

### `#/components/examples/interaction-limit-response`

```json
{
    "value": {
        "limit": "collaborators_only",
        "origin": "organization",
        "expires_at": "2018-08-17T04:18:39Z"
    }
}
```