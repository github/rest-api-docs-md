# Deprecated - List tag protection states for a repository

**Note**: This operation is deprecated and will be removed after August 30th 2024
Use the "[Repository Rulesets](https://docs.github.com/rest/repos/rules#get-all-repository-rulesets)" endpoint instead.

This returns the tag protection states of a repository.

This information is only available to repository administrators.

## Operation Object

```json
{
    "summary": "Deprecated - List tag protection states for a repository",
    "description": "**Note**: This operation is deprecated and will be removed after August 30th 2024\nUse the \"[Repository Rulesets](https://docs.github.com/rest/repos/rules#get-all-repository-rulesets)\" endpoint instead.\n\nThis returns the tag protection states of a repository.\n\nThis information is only available to repository administrators.",
    "tags": [
        "repos"
    ],
    "operationId": "repos/list-tag-protection",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/repos/tags#deprecated---list-tag-protection-states-for-a-repository"
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
                            "$ref": "#/components/schemas/tag-protection"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/tag-protection-items"
                        }
                    }
                }
            }
        },
        "403": {
            "$ref": "#/components/responses/forbidden"
        },
        "404": {
            "$ref": "#/components/responses/not_found"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "repos",
        "subcategory": "tags",
        "deprecationDate": "2024-05-29",
        "removalDate": "2024-08-30"
    },
    "deprecated": true
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

### `#/components/schemas/tag-protection`

```json
{
    "title": "Tag protection",
    "description": "Tag protection",
    "type": "object",
    "properties": {
        "id": {
            "type": "integer",
            "example": 2
        },
        "created_at": {
            "type": "string",
            "example": "2011-01-26T19:01:12Z"
        },
        "updated_at": {
            "type": "string",
            "example": "2011-01-26T19:01:12Z"
        },
        "enabled": {
            "type": "boolean",
            "example": true
        },
        "pattern": {
            "type": "string",
            "example": "v1.*"
        }
    },
    "required": [
        "pattern"
    ]
}
```

### `#/components/examples/tag-protection-items`

```json
{
    "value": [
        {
            "id": 2,
            "pattern": "v1.*"
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