# Get interaction restrictions for a repository

Shows which type of GitHub user can interact with this repository and when the restriction expires. If there are no restrictions, you will see an empty response.

## Operation Object

```json
{
    "summary": "Get interaction restrictions for a repository",
    "description": "Shows which type of GitHub user can interact with this repository and when the restriction expires. If there are no restrictions, you will see an empty response.",
    "tags": [
        "interactions"
    ],
    "operationId": "interactions/get-restrictions-for-repo",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/interactions/repos#get-interaction-restrictions-for-a-repository"
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
                            "$ref": "#/components/examples/interaction-limit-2"
                        }
                    }
                }
            }
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "interactions",
        "subcategory": "repos"
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

### `#/components/examples/interaction-limit-2`

```json
{
    "value": {
        "limit": "collaborators_only",
        "origin": "repository",
        "expires_at": "2018-08-17T04:18:39Z"
    }
}
```