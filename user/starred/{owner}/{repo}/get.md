# Check if a repository is starred by the authenticated user

Whether the authenticated user has starred the repository.

## Operation Object

```json
{
    "summary": "Check if a repository is starred by the authenticated user",
    "description": "Whether the authenticated user has starred the repository.",
    "tags": [
        "activity"
    ],
    "operationId": "activity/check-repo-is-starred-by-authenticated-user",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/activity/starring#check-if-a-repository-is-starred-by-the-authenticated-user"
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
        "204": {
            "description": "Response if this repository is starred by you"
        },
        "404": {
            "description": "Not Found if this repository is not starred by you",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/basic-error"
                    }
                }
            }
        },
        "401": {
            "$ref": "#/components/responses/requires_authentication"
        },
        "304": {
            "$ref": "#/components/responses/not_modified"
        },
        "403": {
            "$ref": "#/components/responses/forbidden"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": false,
        "category": "activity",
        "subcategory": "starring"
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

### `#/components/schemas/basic-error`

```json
{
    "title": "Basic Error",
    "description": "Basic Error",
    "type": "object",
    "properties": {
        "message": {
            "type": "string"
        },
        "documentation_url": {
            "type": "string"
        },
        "url": {
            "type": "string"
        },
        "status": {
            "type": "string"
        }
    }
}
```

### `#/components/responses/requires_authentication`

```json
{
    "description": "Requires authentication",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/basic-error"
            }
        }
    }
}
```

### `#/components/responses/not_modified`

```json
{
    "description": "Not modified"
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