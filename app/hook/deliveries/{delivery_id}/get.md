# Get a delivery for an app webhook

`get /app/hook/deliveries/{delivery_id}`

Returns a delivery for the webhook configured for a GitHub App.

You must use a [JWT](https://docs.github.com/apps/building-github-apps/authenticating-with-github-apps/#authenticating-as-a-github-app) to access this endpoint.

## Operation Object

```json
{
    "summary": "Get a delivery for an app webhook",
    "description": "Returns a delivery for the webhook configured for a GitHub App.\n\nYou must use a [JWT](https://docs.github.com/apps/building-github-apps/authenticating-with-github-apps/#authenticating-as-a-github-app) to access this endpoint.",
    "tags": [
        "apps"
    ],
    "operationId": "apps/get-webhook-delivery",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/apps/webhooks#get-a-delivery-for-an-app-webhook"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/delivery-id"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/hook-delivery"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/hook-delivery"
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

### `#/components/parameters/delivery-id`

```json
{
    "name": "delivery_id",
    "in": "path",
    "required": true,
    "schema": {
        "type": "integer"
    }
}
```

### `#/components/schemas/hook-delivery`

```json
{
    "title": "Webhook delivery",
    "description": "Delivery made by a webhook.",
    "type": "object",
    "properties": {
        "id": {
            "description": "Unique identifier of the delivery.",
            "type": "integer",
            "example": 42
        },
        "guid": {
            "description": "Unique identifier for the event (shared with all deliveries for all webhooks that subscribe to this event).",
            "type": "string",
            "example": "58474f00-b361-11eb-836d-0e4f3503ccbe"
        },
        "delivered_at": {
            "description": "Time when the delivery was delivered.",
            "type": "string",
            "format": "date-time",
            "example": "2021-05-12T20:33:44Z"
        },
        "redelivery": {
            "description": "Whether the delivery is a redelivery.",
            "type": "boolean",
            "example": false
        },
        "duration": {
            "description": "Time spent delivering.",
            "type": "number",
            "example": 0.03
        },
        "status": {
            "description": "Description of the status of the attempted delivery",
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
        },
        "url": {
            "description": "The URL target of the delivery.",
            "type": "string",
            "example": "https://www.example.com"
        },
        "request": {
            "type": "object",
            "properties": {
                "headers": {
                    "description": "The request headers sent with the webhook delivery.",
                    "type": "object",
                    "nullable": true,
                    "additionalProperties": true
                },
                "payload": {
                    "description": "The webhook payload.",
                    "type": "object",
                    "nullable": true,
                    "additionalProperties": true
                }
            },
            "required": [
                "headers",
                "payload"
            ]
        },
        "response": {
            "type": "object",
            "properties": {
                "headers": {
                    "description": "The response headers received when the delivery was made.",
                    "type": "object",
                    "nullable": true,
                    "additionalProperties": true
                },
                "payload": {
                    "description": "The response payload received.",
                    "type": "string",
                    "nullable": true,
                    "additionalProperties": true
                }
            },
            "required": [
                "headers",
                "payload"
            ]
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
        "repository_id",
        "request",
        "response"
    ]
}
```

### `#/components/examples/hook-delivery`

```json
{
    "value": {
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
        "url": "https://www.example.com",
        "throttled_at": "2019-06-03T00:57:16Z",
        "request": {
            "headers": {
                "X-GitHub-Delivery": "0b989ba4-242f-11e5-81e1-c7b6966d2516",
                "X-Hub-Signature-256": "sha256=6dcb09b5b57875f334f61aebed695e2e4193db5e",
                "Accept": "*/*",
                "X-GitHub-Hook-ID": "42",
                "User-Agent": "GitHub-Hookshot/b8c71d8",
                "X-GitHub-Event": "issues",
                "X-GitHub-Hook-Installation-Target-ID": "123",
                "X-GitHub-Hook-Installation-Target-Type": "repository",
                "content-type": "application/json",
                "X-Hub-Signature": "sha1=a84d88e7554fc1fa21bcbc4efae3c782a70d2b9d"
            },
            "payload": {
                "action": "opened",
                "issue": {
                    "body": "foo"
                },
                "repository": {
                    "id": 123
                }
            }
        },
        "response": {
            "headers": {
                "Content-Type": "text/html;charset=utf-8"
            },
            "payload": "ok"
        }
    }
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