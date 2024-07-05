# Get a repository subscription

Gets information about whether the authenticated user is subscribed to the repository.

## Operation Object

```json
{
    "summary": "Get a repository subscription",
    "description": "Gets information about whether the authenticated user is subscribed to the repository.",
    "tags": [
        "activity"
    ],
    "operationId": "activity/get-repo-subscription",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/activity/watching#get-a-repository-subscription"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        }
    ],
    "responses": {
        "200": {
            "description": "if you subscribe to the repository",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/repository-subscription"
                    },
                    "examples": {
                        "response-if-you-subscribe-to-the-repository": {
                            "$ref": "#/components/examples/repository-subscription-response-if-you-subscribe-to-the-repository"
                        }
                    }
                }
            }
        },
        "404": {
            "description": "Not Found if you don't subscribe to the repository"
        },
        "403": {
            "$ref": "#/components/responses/forbidden"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": false,
        "category": "activity",
        "subcategory": "watching"
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

### `#/components/schemas/repository-subscription`

```json
{
    "title": "Repository Invitation",
    "description": "Repository invitations let you manage who you collaborate with.",
    "type": "object",
    "properties": {
        "subscribed": {
            "description": "Determines if notifications should be received from this repository.",
            "type": "boolean",
            "example": true
        },
        "ignored": {
            "description": "Determines if all notifications should be blocked from this repository.",
            "type": "boolean"
        },
        "reason": {
            "type": "string",
            "nullable": true
        },
        "created_at": {
            "type": "string",
            "format": "date-time",
            "example": "2012-10-06T21:34:12Z"
        },
        "url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/repos/octocat/example/subscription"
        },
        "repository_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/repos/octocat/example"
        }
    },
    "required": [
        "created_at",
        "ignored",
        "reason",
        "subscribed",
        "url",
        "repository_url"
    ]
}
```

### `#/components/examples/repository-subscription-response-if-you-subscribe-to-the-repository`

```json
{
    "value": {
        "subscribed": true,
        "ignored": false,
        "reason": null,
        "created_at": "2012-10-06T21:34:12Z",
        "url": "https://api.github.com/repos/octocat/example/subscription",
        "repository_url": "https://api.github.com/repos/octocat/example"
    }
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