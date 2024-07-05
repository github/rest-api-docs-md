# List social accounts for a user

`get /users/{username}/social_accounts`

Lists social media accounts for a user. This endpoint is accessible by anyone.

## Operation Object

```json
{
    "summary": "List social accounts for a user",
    "description": "Lists social media accounts for a user. This endpoint is accessible by anyone.",
    "tags": [
        "users"
    ],
    "operationId": "users/list-social-accounts-for-user",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/users/social-accounts#list-social-accounts-for-a-user"
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
                            "$ref": "#/components/schemas/social-account"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/social-account-items"
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
        "subcategory": "social-accounts"
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

### `#/components/schemas/social-account`

```json
{
    "title": "Social account",
    "description": "Social media account",
    "type": "object",
    "properties": {
        "provider": {
            "type": "string",
            "example": "linkedin"
        },
        "url": {
            "type": "string",
            "example": "https://www.linkedin.com/company/github/"
        }
    },
    "required": [
        "provider",
        "url"
    ]
}
```

### `#/components/examples/social-account-items`

```json
{
    "value": [
        {
            "provider": "twitter",
            "url": "https://twitter.com/github"
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