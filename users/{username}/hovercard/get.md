# Get contextual information for a user

Provides hovercard information. You can find out more about someone in relation to their pull requests, issues, repositories, and organizations.

  The `subject_type` and `subject_id` parameters provide context for the person's hovercard, which returns more information than without the parameters. For example, if you wanted to find out more about `octocat` who owns the `Spoon-Knife` repository, you would use a `subject_type` value of `repository` and a `subject_id` value of `1300192` (the ID of the `Spoon-Knife` repository).

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "Get contextual information for a user",
    "description": "Provides hovercard information. You can find out more about someone in relation to their pull requests, issues, repositories, and organizations.\n\n  The `subject_type` and `subject_id` parameters provide context for the person's hovercard, which returns more information than without the parameters. For example, if you wanted to find out more about `octocat` who owns the `Spoon-Knife` repository, you would use a `subject_type` value of `repository` and a `subject_id` value of `1300192` (the ID of the `Spoon-Knife` repository).\n\nOAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.",
    "tags": [
        "users"
    ],
    "operationId": "users/get-context-for-user",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/users/users#get-contextual-information-for-a-user"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/username"
        },
        {
            "name": "subject_type",
            "description": "Identifies which additional information you'd like to receive about the person's hovercard. Can be `organization`, `repository`, `issue`, `pull_request`. **Required** when using `subject_id`.",
            "in": "query",
            "required": false,
            "schema": {
                "type": "string",
                "enum": [
                    "organization",
                    "repository",
                    "issue",
                    "pull_request"
                ]
            }
        },
        {
            "name": "subject_id",
            "description": "Uses the ID for the `subject_type` you specified. **Required** when using `subject_type`.",
            "in": "query",
            "required": false,
            "schema": {
                "type": "string"
            }
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/hovercard"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/hovercard"
                        }
                    }
                }
            }
        },
        "404": {
            "$ref": "#/components/responses/not_found"
        },
        "422": {
            "$ref": "#/components/responses/validation_failed"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": false,
        "category": "users",
        "subcategory": "users"
    }
}
```

## References

### `#/components/parameters/username`

```json
{
    "name": "username",
    "description": "The handle for the GitHub user account.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "string"
    }
}
```

### `#/components/schemas/hovercard`

```json
{
    "title": "Hovercard",
    "description": "Hovercard",
    "type": "object",
    "properties": {
        "contexts": {
            "type": "array",
            "items": {
                "type": "object",
                "properties": {
                    "message": {
                        "type": "string"
                    },
                    "octicon": {
                        "type": "string"
                    }
                },
                "required": [
                    "message",
                    "octicon"
                ]
            }
        }
    },
    "required": [
        "contexts"
    ]
}
```

### `#/components/examples/hovercard`

```json
{
    "value": {
        "contexts": [
            {
                "message": "Owns this repository",
                "octicon": "repo"
            }
        ]
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