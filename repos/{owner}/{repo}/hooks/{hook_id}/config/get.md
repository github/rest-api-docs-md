# Get a webhook configuration for a repository

Returns the webhook configuration for a repository. To get more information about the webhook, including the `active` state and `events`, use "[Get a repository webhook](/rest/webhooks/repos#get-a-repository-webhook)."

OAuth app tokens and personal access tokens (classic) need the `read:repo_hook` or `repo` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "Get a webhook configuration for a repository",
    "description": "Returns the webhook configuration for a repository. To get more information about the webhook, including the `active` state and `events`, use \"[Get a repository webhook](/rest/webhooks/repos#get-a-repository-webhook).\"\n\nOAuth app tokens and personal access tokens (classic) need the `read:repo_hook` or `repo` scope to use this endpoint.",
    "tags": [
        "repos"
    ],
    "operationId": "repos/get-webhook-config-for-repo",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/repos/webhooks#get-a-webhook-configuration-for-a-repository"
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
                        "$ref": "#/components/schemas/webhook-config"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/webhook-config"
                        }
                    }
                }
            }
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

### `#/components/schemas/webhook-config`

```json
{
    "title": "Webhook Configuration",
    "description": "Configuration object of the webhook",
    "type": "object",
    "properties": {
        "url": {
            "$ref": "#/components/schemas/webhook-config-url"
        },
        "content_type": {
            "$ref": "#/components/schemas/webhook-config-content-type"
        },
        "secret": {
            "$ref": "#/components/schemas/webhook-config-secret"
        },
        "insecure_ssl": {
            "$ref": "#/components/schemas/webhook-config-insecure-ssl"
        }
    }
}
```

### `#/components/examples/webhook-config`

```json
{
    "value": {
        "content_type": "json",
        "insecure_ssl": "0",
        "secret": "********",
        "url": "https://example.com/webhook"
    }
}
```