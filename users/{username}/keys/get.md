# List public keys for a user

Lists the _verified_ public SSH keys for a user. This is accessible by anyone.

## Operation Object

```json
{
    "summary": "List public keys for a user",
    "description": "Lists the _verified_ public SSH keys for a user. This is accessible by anyone.",
    "tags": [
        "users"
    ],
    "operationId": "users/list-public-keys-for-user",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/users/keys#list-public-keys-for-a-user"
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
                            "$ref": "#/components/schemas/key-simple"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/key-simple-items"
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
        "subcategory": "keys"
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

### `#/components/schemas/key-simple`

```json
{
    "title": "Key Simple",
    "description": "Key Simple",
    "type": "object",
    "properties": {
        "id": {
            "type": "integer"
        },
        "key": {
            "type": "string"
        }
    },
    "required": [
        "key",
        "id"
    ]
}
```

### `#/components/examples/key-simple-items`

```json
{
    "value": [
        {
            "id": 1,
            "key": "ssh-rsa AAA..."
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