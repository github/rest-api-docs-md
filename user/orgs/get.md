# List organizations for the authenticated user

`get /user/orgs`

List organizations for the authenticated user.

For OAuth app tokens and personal access tokens (classic), this endpoint only lists organizations that your authorization allows you to operate on in some way (e.g., you can list teams with `read:org` scope, you can publicize your organization membership with `user` scope, etc.). Therefore, this API requires at least `user` or `read:org` scope for OAuth app tokens and personal access tokens (classic). Requests with insufficient scope will receive a `403 Forbidden` response.

## Operation Object

```json
{
    "summary": "List organizations for the authenticated user",
    "description": "List organizations for the authenticated user.\n\nFor OAuth app tokens and personal access tokens (classic), this endpoint only lists organizations that your authorization allows you to operate on in some way (e.g., you can list teams with `read:org` scope, you can publicize your organization membership with `user` scope, etc.). Therefore, this API requires at least `user` or `read:org` scope for OAuth app tokens and personal access tokens (classic). Requests with insufficient scope will receive a `403 Forbidden` response.",
    "tags": [
        "orgs"
    ],
    "operationId": "orgs/list-for-authenticated-user",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/orgs/orgs#list-organizations-for-the-authenticated-user"
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
                            "$ref": "#/components/schemas/organization-simple"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/organization-simple-items"
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
        "category": "orgs",
        "subcategory": "orgs"
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

### `#/components/schemas/organization-simple`

```json
{
    "title": "Organization Simple",
    "description": "A GitHub organization.",
    "type": "object",
    "properties": {
        "login": {
            "type": "string",
            "example": "github"
        },
        "id": {
            "type": "integer",
            "example": 1
        },
        "node_id": {
            "type": "string",
            "example": "MDEyOk9yZ2FuaXphdGlvbjE="
        },
        "url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/orgs/github"
        },
        "repos_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/orgs/github/repos"
        },
        "events_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/orgs/github/events"
        },
        "hooks_url": {
            "type": "string",
            "example": "https://api.github.com/orgs/github/hooks"
        },
        "issues_url": {
            "type": "string",
            "example": "https://api.github.com/orgs/github/issues"
        },
        "members_url": {
            "type": "string",
            "example": "https://api.github.com/orgs/github/members{/member}"
        },
        "public_members_url": {
            "type": "string",
            "example": "https://api.github.com/orgs/github/public_members{/member}"
        },
        "avatar_url": {
            "type": "string",
            "example": "https://github.com/images/error/octocat_happy.gif"
        },
        "description": {
            "type": "string",
            "example": "A great organization",
            "nullable": true
        }
    },
    "required": [
        "login",
        "url",
        "id",
        "node_id",
        "repos_url",
        "events_url",
        "hooks_url",
        "issues_url",
        "members_url",
        "public_members_url",
        "avatar_url",
        "description"
    ]
}
```

### `#/components/examples/organization-simple-items`

```json
{
    "value": [
        {
            "login": "github",
            "id": 1,
            "node_id": "MDEyOk9yZ2FuaXphdGlvbjE=",
            "url": "https://api.github.com/orgs/github",
            "repos_url": "https://api.github.com/orgs/github/repos",
            "events_url": "https://api.github.com/orgs/github/events",
            "hooks_url": "https://api.github.com/orgs/github/hooks",
            "issues_url": "https://api.github.com/orgs/github/issues",
            "members_url": "https://api.github.com/orgs/github/members{/member}",
            "public_members_url": "https://api.github.com/orgs/github/public_members{/member}",
            "avatar_url": "https://github.com/images/error/octocat_happy.gif",
            "description": "A great organization"
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