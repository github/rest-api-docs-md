# List repository webhooks

`get /repos/{owner}/{repo}/hooks`

Lists webhooks for a repository. `last response` may return null if there have not been any deliveries within 30 days.

## Operation Object

```json
{
    "summary": "List repository webhooks",
    "description": "Lists webhooks for a repository. `last response` may return null if there have not been any deliveries within 30 days.",
    "tags": [
        "repos"
    ],
    "operationId": "repos/list-webhooks",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/repos/webhooks#list-repository-webhooks"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
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
                            "$ref": "#/components/schemas/hook"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/hook-items"
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
        "404": {
            "$ref": "#/components/responses/not_found"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "repos",
        "subcategory": "webhooks"
    }
}
```

## References

### `#/components/parameters/owner`

```json
{
    "name": "owner",
    "description": "The account owner of the repository. The name is not case sensitive.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "string"
    }
}
```

### `#/components/parameters/repo`

```json
{
    "name": "repo",
    "description": "The name of the repository without the `.git` extension. The name is not case sensitive.",
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

### `#/components/schemas/hook`

```json
{
    "title": "Webhook",
    "description": "Webhooks for repositories.",
    "type": "object",
    "properties": {
        "type": {
            "type": "string"
        },
        "id": {
            "description": "Unique identifier of the webhook.",
            "example": 42,
            "type": "integer"
        },
        "name": {
            "description": "The name of a valid service, use 'web' for a webhook.",
            "example": "web",
            "type": "string"
        },
        "active": {
            "description": "Determines whether the hook is actually triggered on pushes.",
            "type": "boolean",
            "example": true
        },
        "events": {
            "description": "Determines what events the hook is triggered for. Default: ['push'].",
            "type": "array",
            "items": {
                "type": "string"
            },
            "example": [
                "push",
                "pull_request"
            ]
        },
        "config": {
            "$ref": "#/components/schemas/webhook-config"
        },
        "updated_at": {
            "type": "string",
            "format": "date-time",
            "example": "2011-09-06T20:39:23Z"
        },
        "created_at": {
            "type": "string",
            "format": "date-time",
            "example": "2011-09-06T17:26:27Z"
        },
        "url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/repos/octocat/Hello-World/hooks/1"
        },
        "test_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/repos/octocat/Hello-World/hooks/1/test"
        },
        "ping_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/repos/octocat/Hello-World/hooks/1/pings"
        },
        "deliveries_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/repos/octocat/Hello-World/hooks/1/deliveries"
        },
        "last_response": {
            "$ref": "#/components/schemas/hook-response"
        }
    },
    "required": [
        "id",
        "url",
        "type",
        "name",
        "active",
        "events",
        "config",
        "ping_url",
        "created_at",
        "updated_at",
        "last_response",
        "test_url"
    ]
}
```

### `#/components/examples/hook-items`

```json
{
    "value": [
        {
            "type": "Repository",
            "id": 12345678,
            "name": "web",
            "active": true,
            "events": [
                "push",
                "pull_request"
            ],
            "config": {
                "content_type": "json",
                "insecure_ssl": "0",
                "url": "https://example.com/webhook"
            },
            "updated_at": "2019-06-03T00:57:16Z",
            "created_at": "2019-06-03T00:57:16Z",
            "url": "https://api.github.com/repos/octocat/Hello-World/hooks/12345678",
            "test_url": "https://api.github.com/repos/octocat/Hello-World/hooks/12345678/test",
            "ping_url": "https://api.github.com/repos/octocat/Hello-World/hooks/12345678/pings",
            "deliveries_url": "https://api.github.com/repos/octocat/Hello-World/hooks/12345678/deliveries",
            "last_response": {
                "code": null,
                "status": "unused",
                "message": null
            }
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