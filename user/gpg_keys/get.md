# List GPG keys for the authenticated user

`get /user/gpg_keys`

Lists the current user's GPG keys.

OAuth app tokens and personal access tokens (classic) need the `read:gpg_key` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "List GPG keys for the authenticated user",
    "description": "Lists the current user's GPG keys.\n\nOAuth app tokens and personal access tokens (classic) need the `read:gpg_key` scope to use this endpoint.",
    "tags": [
        "users"
    ],
    "operationId": "users/list-gpg-keys-for-authenticated-user",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/users/gpg-keys#list-gpg-keys-for-the-authenticated-user"
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
                            "$ref": "#/components/schemas/gpg-key"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/gpg-key-items"
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
        "subcategory": "gpg-keys"
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

### `#/components/schemas/gpg-key`

```json
{
    "title": "GPG Key",
    "description": "A unique encryption key",
    "type": "object",
    "properties": {
        "id": {
            "type": "integer",
            "format": "int64",
            "example": 3
        },
        "name": {
            "type": "string",
            "example": "Octocat's GPG Key",
            "nullable": true
        },
        "primary_key_id": {
            "type": "integer",
            "nullable": true
        },
        "key_id": {
            "type": "string",
            "example": "3262EFF25BA0D270"
        },
        "public_key": {
            "type": "string",
            "example": "xsBNBFayYZ..."
        },
        "emails": {
            "type": "array",
            "example": [
                {
                    "email": "octocat@users.noreply.github.com",
                    "verified": true
                }
            ],
            "items": {
                "type": "object",
                "properties": {
                    "email": {
                        "type": "string"
                    },
                    "verified": {
                        "type": "boolean"
                    }
                }
            }
        },
        "subkeys": {
            "type": "array",
            "example": [
                {
                    "id": 4,
                    "primary_key_id": 3,
                    "key_id": "4A595D4C72EE49C7",
                    "public_key": "zsBNBFayYZ...",
                    "emails": [],
                    "can_sign": false,
                    "can_encrypt_comms": true,
                    "can_encrypt_storage": true,
                    "can_certify": false,
                    "created_at": "2016-03-24T11:31:04-06:00",
                    "expires_at": null,
                    "revoked": false
                }
            ],
            "items": {
                "type": "object",
                "properties": {
                    "id": {
                        "type": "integer",
                        "format": "int64"
                    },
                    "primary_key_id": {
                        "type": "integer"
                    },
                    "key_id": {
                        "type": "string"
                    },
                    "public_key": {
                        "type": "string"
                    },
                    "emails": {
                        "type": "array",
                        "items": {
                            "type": "object",
                            "properties": {
                                "email": {
                                    "type": "string"
                                },
                                "verified": {
                                    "type": "boolean"
                                }
                            }
                        }
                    },
                    "subkeys": {
                        "type": "array",
                        "items": {}
                    },
                    "can_sign": {
                        "type": "boolean"
                    },
                    "can_encrypt_comms": {
                        "type": "boolean"
                    },
                    "can_encrypt_storage": {
                        "type": "boolean"
                    },
                    "can_certify": {
                        "type": "boolean"
                    },
                    "created_at": {
                        "type": "string"
                    },
                    "expires_at": {
                        "type": "string",
                        "nullable": true
                    },
                    "raw_key": {
                        "type": "string",
                        "nullable": true
                    },
                    "revoked": {
                        "type": "boolean"
                    }
                }
            }
        },
        "can_sign": {
            "type": "boolean",
            "example": true
        },
        "can_encrypt_comms": {
            "type": "boolean"
        },
        "can_encrypt_storage": {
            "type": "boolean"
        },
        "can_certify": {
            "type": "boolean",
            "example": true
        },
        "created_at": {
            "type": "string",
            "format": "date-time",
            "example": "2016-03-24T11:31:04-06:00"
        },
        "expires_at": {
            "type": "string",
            "format": "date-time",
            "nullable": true
        },
        "revoked": {
            "type": "boolean",
            "example": true
        },
        "raw_key": {
            "type": "string",
            "nullable": true
        }
    },
    "required": [
        "id",
        "primary_key_id",
        "key_id",
        "raw_key",
        "public_key",
        "created_at",
        "expires_at",
        "can_sign",
        "can_encrypt_comms",
        "can_encrypt_storage",
        "can_certify",
        "emails",
        "subkeys",
        "revoked"
    ]
}
```

### `#/components/examples/gpg-key-items`

```json
{
    "value": [
        {
            "id": 3,
            "name": "Octocat's GPG Key",
            "primary_key_id": 2,
            "key_id": "3262EFF25BA0D270",
            "public_key": "xsBNBFayYZ...",
            "emails": [
                {
                    "email": "octocat@users.noreply.github.com",
                    "verified": true
                }
            ],
            "subkeys": [
                {
                    "id": 4,
                    "primary_key_id": 3,
                    "key_id": "4A595D4C72EE49C7",
                    "public_key": "zsBNBFayYZ...",
                    "emails": [],
                    "can_sign": false,
                    "can_encrypt_comms": true,
                    "can_encrypt_storage": true,
                    "can_certify": false,
                    "created_at": "2016-03-24T11:31:04-06:00",
                    "expires_at": "2016-03-24T11:31:04-07:00",
                    "revoked": false
                }
            ],
            "can_sign": true,
            "can_encrypt_comms": false,
            "can_encrypt_storage": false,
            "can_certify": true,
            "created_at": "2016-03-24T11:31:04-06:00",
            "expires_at": "2016-03-24T11:31:04-07:00",
            "revoked": false,
            "raw_key": "string"
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