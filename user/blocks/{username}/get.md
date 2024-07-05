# Check if a user is blocked by the authenticated user

Returns a 204 if the given user is blocked by the authenticated user. Returns a 404 if the given user is not blocked by the authenticated user, or if the given user account has been identified as spam by GitHub.

## Operation Object

```json
{
    "summary": "Check if a user is blocked by the authenticated user",
    "description": "Returns a 204 if the given user is blocked by the authenticated user. Returns a 404 if the given user is not blocked by the authenticated user, or if the given user account has been identified as spam by GitHub.",
    "tags": [
        "users"
    ],
    "operationId": "users/check-blocked",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/users/blocking#check-if-a-user-is-blocked-by-the-authenticated-user"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/username"
        }
    ],
    "responses": {
        "204": {
            "description": "If the user is blocked"
        },
        "404": {
            "description": "If the user is not blocked",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/basic-error"
                    }
                }
            }
        },
        "304": {
            "$ref": "#/components/responses/not_modified"
        },
        "403": {
            "$ref": "#/components/responses/forbidden"
        },
        "401": {
            "$ref": "#/components/responses/requires_authentication"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": false,
        "category": "users",
        "subcategory": "blocking"
    }
}
```

## References

### `#/components/parameters/username`

```json
{
    "name": "username",
    "description": "The handle for the GitHub user account.",
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