# List public SSH keys for the authenticated user

Lists the public SSH keys for the authenticated user's GitHub account.

OAuth app tokens and personal access tokens (classic) need the `read:public_key` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "List public SSH keys for the authenticated user",
    "description": "Lists the public SSH keys for the authenticated user's GitHub account.\n\nOAuth app tokens and personal access tokens (classic) need the `read:public_key` scope to use this endpoint.",
    "tags": [
        "users"
    ],
    "operationId": "users/list-public-ssh-keys-for-authenticated-user",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/users/keys#list-public-ssh-keys-for-the-authenticated-user"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/per-page"
        },
        {
            "$ref": "#/components/parameters/page"
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
                            "$ref": "#/components/schemas/key"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/key-items"
                        }
                    }
                }
            },
            "headers": {
                "Link": {
                    "$ref": "#/components/headers/link"
                }
            }
        },
        "304": {
            "$ref": "#/components/responses/not_modified"
        },
        "404": {
            "$ref": "#/components/responses/not_found"
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

### `#/components/parameters/per-page`

```json
{
    "name": "per_page",
    "description": "The number of results per page (max 100). For more information, see \"[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api).\"",
    "in": "query",
    "schema": {
        "type": "integer",
        "default": 30
    }
}
```

### `#/components/parameters/page`

```json
{
    "name": "page",
    "description": "The page number of the results to fetch. For more information, see \"[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api).\"",
    "in": "query",
    "schema": {
        "type": "integer",
        "default": 1
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

### `#/components/examples/key-items`

```json
{
    "value": [
        {
            "key": "2Sg8iYjAxxmI2LvUXpJjkYrMxURPc8r+dB7TJyvv1234",
            "id": 2,
            "url": "https://api.github.com/user/keys/2",
            "title": "ssh-rsa AAAAB3NzaC1yc2EAAA",
            "created_at": "2020-06-11T21:31:57Z",
            "verified": false,
            "read_only": false
        },
        {
            "key": "2Sg8iYjAxxmI2LvUXpJjkYrMxURPc8r+dB7TJy931234",
            "id": 3,
            "url": "https://api.github.com/user/keys/3",
            "title": "ssh-rsa AAAAB3NzaC1yc2EAAB",
            "created_at": "2020-07-11T21:31:57Z",
            "verified": false,
            "read_only": false
        }
    ]
}
```

### `#/components/headers/link`

```json
{
    "example": "<https://api.github.com/resource?page=2>; rel=\"next\", <https://api.github.com/resource?page=5>; rel=\"last\"",
    "schema": {
        "type": "string"
    }
}
```

### `#/components/responses/not_modified`

```json
{
    "description": "Not modified"
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