# List email addresses for the authenticated user

Lists all of your email addresses, and specifies which one is visible
to the public.

OAuth app tokens and personal access tokens (classic) need the `user:email` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "List email addresses for the authenticated user",
    "description": "Lists all of your email addresses, and specifies which one is visible\nto the public.\n\nOAuth app tokens and personal access tokens (classic) need the `user:email` scope to use this endpoint.",
    "tags": [
        "users"
    ],
    "operationId": "users/list-emails-for-authenticated-user",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/users/emails#list-email-addresses-for-the-authenticated-user"
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
                            "$ref": "#/components/schemas/email"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/email-items-2"
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
        "subcategory": "emails"
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

### `#/components/schemas/email`

```json
{
    "title": "Email",
    "description": "Email",
    "type": "object",
    "properties": {
        "email": {
            "type": "string",
            "format": "email",
            "example": "octocat@github.com"
        },
        "primary": {
            "type": "boolean",
            "example": true
        },
        "verified": {
            "type": "boolean",
            "example": true
        },
        "visibility": {
            "type": "string",
            "example": "public",
            "nullable": true
        }
    },
    "required": [
        "email",
        "primary",
        "verified",
        "visibility"
    ]
}
```

### `#/components/examples/email-items-2`

```json
{
    "value": [
        {
            "email": "octocat@github.com",
            "verified": true,
            "primary": true,
            "visibility": "public"
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