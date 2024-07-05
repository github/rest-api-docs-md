# Get an organization webhook

`get /orgs/{org}/hooks/{hook_id}`

Returns a webhook configured in an organization. To get only the webhook
`config` properties, see "[Get a webhook configuration for an organization](/rest/orgs/webhooks#get-a-webhook-configuration-for-an-organization).

You must be an organization owner to use this endpoint.

OAuth app tokens and personal access tokens (classic) need `admin:org_hook` scope. OAuth apps cannot list, view, or edit
webhooks that they did not create and users cannot list, view, or edit webhooks that were created by OAuth apps.

## Operation Object

```json
{
    "summary": "Get an organization webhook",
    "description": "Returns a webhook configured in an organization. To get only the webhook\n`config` properties, see \"[Get a webhook configuration for an organization](/rest/orgs/webhooks#get-a-webhook-configuration-for-an-organization).\n\nYou must be an organization owner to use this endpoint.\n\nOAuth app tokens and personal access tokens (classic) need `admin:org_hook` scope. OAuth apps cannot list, view, or edit\nwebhooks that they did not create and users cannot list, view, or edit webhooks that were created by OAuth apps.",
    "tags": [
        "orgs"
    ],
    "operationId": "orgs/get-webhook",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/orgs/webhooks#get-an-organization-webhook"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/org"
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
                        "$ref": "#/components/schemas/org-hook"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/org-hook"
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
        "category": "orgs",
        "subcategory": "webhooks"
    }
}
```

## References

### `#/components/parameters/org`

```json
{
    "name": "org",
    "description": "The organization name. The name is not case sensitive.",
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

### `#/components/schemas/org-hook`

```json
{
    "title": "Org Hook",
    "description": "Org Hook",
    "type": "object",
    "properties": {
        "id": {
            "type": "integer",
            "example": 1
        },
        "url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/orgs/octocat/hooks/1"
        },
        "ping_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/orgs/octocat/hooks/1/pings"
        },
        "deliveries_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/orgs/octocat/hooks/1/deliveries"
        },
        "name": {
            "type": "string",
            "example": "web"
        },
        "events": {
            "type": "array",
            "example": [
                "push",
                "pull_request"
            ],
            "items": {
                "type": "string"
            }
        },
        "active": {
            "type": "boolean",
            "example": true
        },
        "config": {
            "type": "object",
            "properties": {
                "url": {
                    "type": "string",
                    "example": "\"http://example.com/2\""
                },
                "insecure_ssl": {
                    "type": "string",
                    "example": "\"0\""
                },
                "content_type": {
                    "type": "string",
                    "example": "\"form\""
                },
                "secret": {
                    "type": "string",
                    "example": "\"********\""
                }
            }
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
        "type": {
            "type": "string"
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
        "updated_at"
    ]
}
```

### `#/components/examples/org-hook`

```json
{
    "value": {
        "id": 1,
        "url": "https://api.github.com/orgs/octocat/hooks/1",
        "ping_url": "https://api.github.com/orgs/octocat/hooks/1/pings",
        "deliveries_url": "https://api.github.com/orgs/octocat/hooks/1/deliveries",
        "name": "web",
        "events": [
            "push",
            "pull_request"
        ],
        "active": true,
        "config": {
            "url": "http://example.com",
            "content_type": "json"
        },
        "updated_at": "2011-09-06T20:39:23Z",
        "created_at": "2011-09-06T17:26:27Z",
        "type": "Organization"
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