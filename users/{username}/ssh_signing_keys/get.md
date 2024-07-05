# List SSH signing keys for a user

`get /users/{username}/ssh_signing_keys`

Lists the SSH signing keys for a user. This operation is accessible by anyone.

## Operation Object

```json
{
    "summary": "List SSH signing keys for a user",
    "description": "Lists the SSH signing keys for a user. This operation is accessible by anyone.",
    "tags": [
        "users"
    ],
    "operationId": "users/list-ssh-signing-keys-for-user",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/users/ssh-signing-keys#list-ssh-signing-keys-for-a-user"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/username"
        },
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
                            "$ref": "#/components/schemas/ssh-signing-key"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/ssh-signing-key-items"
                        }
                    }
                }
            },
            "headers": {
                "Link": {
                    "$ref": "#/components/headers/link"
                }
            }
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "users",
        "subcategory": "ssh-signing-keys"
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

### `#/components/examples/ssh-signing-key-items`

```json
{
    "value": [
        {
            "key": "2Sg8iYjAxxmI2LvUXpJjkYrMxURPc8r+dB7TJyvv1234",
            "id": 2,
            "url": "https://api.github.com/user/keys/2",
            "title": "ssh-rsa AAAAB3NzaC1yc2EAAA",
            "created_at": "2020-06-11T21:31:57Z"
        },
        {
            "key": "2Sg8iYjAxxmI2LvUXpJjkYrMxURPc8r+dB7TJy931234",
            "id": 3,
            "url": "https://api.github.com/user/keys/3",
            "title": "ssh-rsa AAAAB3NzaC1yc2EAAB",
            "created_at": "2020-07-11T21:31:57Z"
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