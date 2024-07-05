# Get an SSH signing key for the authenticated user

Gets extended details for an SSH signing key.

OAuth app tokens and personal access tokens (classic) need the `read:ssh_signing_key` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "Get an SSH signing key for the authenticated user",
    "description": "Gets extended details for an SSH signing key.\n\nOAuth app tokens and personal access tokens (classic) need the `read:ssh_signing_key` scope to use this endpoint.",
    "tags": [
        "users"
    ],
    "operationId": "users/get-ssh-signing-key-for-authenticated-user",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/users/ssh-signing-keys#get-an-ssh-signing-key-for-the-authenticated-user"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/ssh-signing-key-id"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/ssh-signing-key"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/ssh-signing-key"
                        }
                    }
                }
            }
        },
        "404": {
            "$ref": "#/components/responses/not_found"
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
        "subcategory": "ssh-signing-keys"
    }
}
```

## References

### `#/components/parameters/ssh-signing-key-id`

```json
{
    "name": "ssh_signing_key_id",
    "description": "The unique identifier of the SSH signing key.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "integer"
    }
}
```

### `#/components/schemas/ssh-signing-key`

```json
{
    "title": "SSH Signing Key",
    "description": "A public SSH key used to sign Git commits",
    "type": "object",
    "properties": {
        "key": {
            "type": "string"
        },
        "id": {
            "type": "integer"
        },
        "title": {
            "type": "string"
        },
        "created_at": {
            "type": "string",
            "format": "date-time"
        }
    },
    "required": [
        "key",
        "id",
        "title",
        "created_at"
    ]
}
```

### `#/components/examples/ssh-signing-key`

```json
{
    "value": {
        "key": "2Sg8iYjAxxmI2LvUXpJjkYrMxURPc8r+dB7TJyvv1234",
        "id": 2,
        "url": "https://api.github.com/user/keys/2",
        "title": "ssh-rsa AAAAB3NzaC1yc2EAAA",
        "created_at": "2020-06-11T21:31:57Z"
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