# List deliveries for an app webhook

`get /app/hook/deliveries`

Returns a list of webhook deliveries for the webhook configured for a GitHub App.

You must use a [JWT](https://docs.github.com/apps/building-github-apps/authenticating-with-github-apps/#authenticating-as-a-github-app) to access this endpoint.

## Operation Object

```json
{
    "summary": "List deliveries for an app webhook",
    "description": "Returns a list of webhook deliveries for the webhook configured for a GitHub App.\n\nYou must use a [JWT](https://docs.github.com/apps/building-github-apps/authenticating-with-github-apps/#authenticating-as-a-github-app) to access this endpoint.",
    "tags": [
        "apps"
    ],
    "operationId": "apps/list-webhook-deliveries",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/apps/webhooks#list-deliveries-for-an-app-webhook"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/per-page"
        },
        {
            "$ref": "#/components/parameters/cursor"
        },
        {
            "name": "redelivery",
            "in": "query",
            "required": false,
            "schema": {
                "type": "boolean"
            }
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
                            "$ref": "#/components/schemas/hook-delivery-item"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/hook-delivery-items"
                        }
                    }
                }
            }
        },
        "400": {
            "$ref": "#/components/responses/bad_request"
        },
        "422": {
            "$ref": "#/components/responses/validation_failed"
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

### `#/components/parameters/cursor`

```json
{
    "name": "cursor",
    "description": "Used for pagination: the starting delivery from which the page of deliveries is fetched. Refer to the `link` header for the next and previous page cursors.",
    "in": "query",
    "required": false,
    "schema": {
        "type": "string"
    }
}
```

### `#/components/schemas/hook-delivery-item`

```json
{
    "title": "Simple webhook delivery",
    "description": "Delivery made by a webhook, without request and response information.",
    "type": "object",
    "properties": {
        "id": {
            "description": "Unique identifier of the webhook delivery.",
            "type": "integer",
            "example": 42
        },
        "guid": {
            "description": "Unique identifier for the event (shared with all deliveries for all webhooks that subscribe to this event).",
            "type": "string",
            "example": "58474f00-b361-11eb-836d-0e4f3503ccbe"
        },
        "delivered_at": {
            "description": "Time when the webhook delivery occurred.",
            "type": "string",
            "format": "date-time",
            "example": "2021-05-12T20:33:44Z"
        },
        "redelivery": {
            "description": "Whether the webhook delivery is a redelivery.",
            "type": "boolean",
            "example": false
        },
        "duration": {
            "description": "Time spent delivering.",
            "type": "number",
            "example": 0.03
        },
        "status": {
            "description": "Describes the response returned after attempting the delivery.",
            "type": "string",
            "example": "failed to connect"
        },
        "status_code": {
            "description": "Status code received when delivery was made.",
            "type": "integer",
            "example": 502
        },
        "event": {
            "description": "The event that triggered the delivery.",
            "type": "string",
            "example": "issues"
        },
        "action": {
            "description": "The type of activity for the event that triggered the delivery.",
            "type": "string",
            "example": "opened",
            "nullable": true
        },
        "installation_id": {
            "description": "The id of the GitHub App installation associated with this event.",
            "type": "integer",
            "example": 123,
            "nullable": true
        },
        "repository_id": {
            "description": "The id of the repository associated with this event.",
            "type": "integer",
            "example": 123,
            "nullable": true
        },
        "throttled_at": {
            "description": "Time when the webhook delivery was throttled.",
            "type": "string",
            "format": "date-time",
            "example": "2021-05-12T20:33:44Z",
            "nullable": true
        }
    },
    "required": [
        "id",
        "guid",
        "delivered_at",
        "redelivery",
        "duration",
        "status",
        "status_code",
        "event",
        "action",
        "installation_id",
        "repository_id"
    ]
}
```

### `#/components/examples/hook-delivery-items`

```json
{
    "value": [
        {
            "id": 12345678,
            "guid": "0b989ba4-242f-11e5-81e1-c7b6966d2516",
            "delivered_at": "2019-06-03T00:57:16Z",
            "redelivery": false,
            "duration": 0.27,
            "status": "OK",
            "status_code": 200,
            "event": "issues",
            "action": "opened",
            "installation_id": 123,
            "repository_id": 456,
            "throttled_at": "2019-06-03T00:57:16Z"
        },
        {
            "id": 123456789,
            "guid": "0b989ba4-242f-11e5-81e1-c7b6966d2516",
            "delivered_at": "2019-06-04T00:57:16Z",
            "redelivery": true,
            "duration": 0.28,
            "status": "OK",
            "status_code": 200,
            "event": "issues",
            "action": "opened",
            "installation_id": 123,
            "repository_id": 456,
            "throttled_at": null
        }
    ]
}
```

### `#/components/responses/bad_request`

```json
{
    "description": "Bad Request",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/basic-error"
            }
        },
        "application/scim+json": {
            "schema": {
                "$ref": "#/components/schemas/scim-error"
            }
        }
    }
}
```

### `#/components/responses/validation_failed`

```json
{
    "description": "Validation failed, or the endpoint has been spammed.",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/validation-error"
            }
        }
    }
}
```