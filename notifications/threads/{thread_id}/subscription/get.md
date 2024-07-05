# Get a thread subscription for the authenticated user

This checks to see if the current user is subscribed to a thread. You can also [get a repository subscription](https://docs.github.com/rest/activity/watching#get-a-repository-subscription).

Note that subscriptions are only generated if a user is participating in a conversation--for example, they've replied to the thread, were **@mentioned**, or manually subscribe to a thread.

## Operation Object

```json
{
    "summary": "Get a thread subscription for the authenticated user",
    "description": "This checks to see if the current user is subscribed to a thread. You can also [get a repository subscription](https://docs.github.com/rest/activity/watching#get-a-repository-subscription).\n\nNote that subscriptions are only generated if a user is participating in a conversation--for example, they've replied to the thread, were **@mentioned**, or manually subscribe to a thread.",
    "tags": [
        "activity"
    ],
    "operationId": "activity/get-thread-subscription-for-authenticated-user",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/activity/notifications#get-a-thread-subscription-for-the-authenticated-user"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/thread-id"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/thread-subscription"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/thread-subscription"
                        }
                    }
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
        "category": "activity",
        "subcategory": "notifications"
    }
}
```

## References

### `#/components/parameters/thread-id`

```json
{
    "name": "thread_id",
    "description": "The unique identifier of the notification thread. This corresponds to the value returned in the `id` field when you retrieve notifications (for example with the [`GET /notifications` operation](https://docs.github.com/rest/activity/notifications#list-notifications-for-the-authenticated-user)).",
    "in": "path",
    "required": true,
    "schema": {
        "type": "integer"
    }
}
```

### `#/components/schemas/thread-subscription`

```json
{
    "title": "Thread Subscription",
    "description": "Thread Subscription",
    "type": "object",
    "properties": {
        "subscribed": {
            "type": "boolean",
            "example": true
        },
        "ignored": {
            "type": "boolean"
        },
        "reason": {
            "type": "string",
            "nullable": true
        },
        "created_at": {
            "type": "string",
            "format": "date-time",
            "example": "2012-10-06T21:34:12Z",
            "nullable": true
        },
        "url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/notifications/threads/1/subscription"
        },
        "thread_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/notifications/threads/1"
        },
        "repository_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/repos/1"
        }
    },
    "required": [
        "created_at",
        "ignored",
        "reason",
        "url",
        "subscribed"
    ]
}
```

### `#/components/examples/thread-subscription`

```json
{
    "value": {
        "subscribed": true,
        "ignored": false,
        "reason": null,
        "created_at": "2012-10-06T21:34:12Z",
        "url": "https://api.github.com/notifications/threads/1/subscription",
        "thread_url": "https://api.github.com/notifications/threads/1"
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