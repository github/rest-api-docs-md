# Get a webhook configuration for an app

Returns the webhook configuration for a GitHub App. For more information about configuring a webhook for your app, see "[Creating a GitHub App](/developers/apps/creating-a-github-app)."

You must use a [JWT](https://docs.github.com/apps/building-github-apps/authenticating-with-github-apps/#authenticating-as-a-github-app) to access this endpoint.

## Operation Object

```json
{
    "summary": "Get a webhook configuration for an app",
    "description": "Returns the webhook configuration for a GitHub App. For more information about configuring a webhook for your app, see \"[Creating a GitHub App](/developers/apps/creating-a-github-app).\"\n\nYou must use a [JWT](https://docs.github.com/apps/building-github-apps/authenticating-with-github-apps/#authenticating-as-a-github-app) to access this endpoint.",
    "tags": [
        "apps"
    ],
    "operationId": "apps/get-webhook-config-for-app",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/apps/webhooks#get-a-webhook-configuration-for-an-app"
    },
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
        "enabledForGitHubApps": false,
        "category": "apps",
        "subcategory": "webhooks"
    }
}
```

## References

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