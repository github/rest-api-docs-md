# Get a public SSH key for the authenticated user

`get /user/keys/{key_id}`

View extended details for a single public SSH key.

OAuth app tokens and personal access tokens (classic) need the `read:public_key` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "Get a public SSH key for the authenticated user",
    "description": "View extended details for a single public SSH key.\n\nOAuth app tokens and personal access tokens (classic) need the `read:public_key` scope to use this endpoint.",
    "tags": [
        "users"
    ],
    "operationId": "users/get-public-ssh-key-for-authenticated-user",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/users/keys#get-a-public-ssh-key-for-the-authenticated-user"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/key-id"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/key"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/key"
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
        "subcategory": "keys"
    }
}
```

## References

### `#/components/parameters/key-id`

```json
{
    "name": "key_id",
    "description": "The unique identifier of the key.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "integer"
    }
}
```

### `#/components/schemas/key`

```json
{
    "title": "Key",
    "description": "Key",
    "type": "object",
    "properties": {
        "key": {
            "type": "string"
        },
        "id": {
            "type": "integer",
            "format": "int64"
        },
        "url": {
            "type": "string"
        },
        "title": {
            "type": "string"
        },
        "created_at": {
            "type": "string",
            "format": "date-time"
        },
        "verified": {
            "type": "boolean"
        },
        "read_only": {
            "type": "boolean"
        }
    },
    "required": [
        "key",
        "id",
        "url",
        "title",
        "created_at",
        "verified",
        "read_only"
    ]
}
```

### `#/components/examples/key`

```json
{
    "value": {
        "key": "2Sg8iYjAxxmI2LvUXpJjkYrMxURPc8r+dB7TJyvv1234",
        "id": 2,
        "url": "https://api.github.com/user/keys/2",
        "title": "ssh-rsa AAAAB3NzaC1yc2EAAA",
        "created_at": "2020-06-11T21:31:57Z",
        "verified": false,
        "read_only": false
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