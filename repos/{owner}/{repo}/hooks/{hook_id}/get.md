# Get a repository webhook

Returns a webhook configured in a repository. To get only the webhook `config` properties, see "[Get a webhook configuration for a repository](/rest/webhooks/repo-config#get-a-webhook-configuration-for-a-repository)."

## Operation Object

```json
{
    "summary": "Get a repository webhook",
    "description": "Returns a webhook configured in a repository. To get only the webhook `config` properties, see \"[Get a webhook configuration for a repository](/rest/webhooks/repo-config#get-a-webhook-configuration-for-a-repository).\"",
    "tags": [
        "repos"
    ],
    "operationId": "repos/get-webhook",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/repos/webhooks#get-a-repository-webhook"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "$ref": "#/components/parameters/hook-id"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/hook"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/hook"
                        }
                    }
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

### `#/components/parameters/hook-id`

```json
{
    "name": "hook_id",
    "description": "The unique identifier of the hook. You can find this value in the `X-GitHub-Hook-ID` header of a webhook delivery.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "integer"
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

### `#/components/examples/hook`

```json
{
    "value": {
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