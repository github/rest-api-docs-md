# Get interaction restrictions for an organization

Shows which type of GitHub user can interact with this organization and when the restriction expires. If there is no restrictions, you will see an empty response.

## Operation Object

```json
{
    "summary": "Get interaction restrictions for an organization",
    "description": "Shows which type of GitHub user can interact with this organization and when the restriction expires. If there is no restrictions, you will see an empty response.",
    "tags": [
        "interactions"
    ],
    "operationId": "interactions/get-restrictions-for-org",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/interactions/orgs#get-interaction-restrictions-for-an-organization"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/org"
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
                            "$ref": "#/components/examples/interaction-limit-response"
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
        "subcategory": "orgs"
    }
}
```

## References

### `#/components/parameters/org`

```json
{
    "name": "org",
    "description": "The organization name. The name is not case sensitive.",
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