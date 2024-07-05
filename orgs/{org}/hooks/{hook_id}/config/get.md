# Get a webhook configuration for an organization

`get /orgs/{org}/hooks/{hook_id}/config`

Returns the webhook configuration for an organization. To get more information about the webhook, including the `active` state and `events`, use "[Get an organization webhook ](/rest/orgs/webhooks#get-an-organization-webhook)."

You must be an organization owner to use this endpoint.

OAuth app tokens and personal access tokens (classic) need `admin:org_hook` scope. OAuth apps cannot list, view, or edit
webhooks that they did not create and users cannot list, view, or edit webhooks that were created by OAuth apps.

## Operation Object

```json
{
    "summary": "Get a webhook configuration for an organization",
    "description": "Returns the webhook configuration for an organization. To get more information about the webhook, including the `active` state and `events`, use \"[Get an organization webhook ](/rest/orgs/webhooks#get-an-organization-webhook).\"\n\nYou must be an organization owner to use this endpoint.\n\nOAuth app tokens and personal access tokens (classic) need `admin:org_hook` scope. OAuth apps cannot list, view, or edit\nwebhooks that they did not create and users cannot list, view, or edit webhooks that were created by OAuth apps.",
    "tags": [
        "orgs"
    ],
    "operationId": "orgs/get-webhook-config-for-org",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/orgs/webhooks#get-a-webhook-configuration-for-an-organization"
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