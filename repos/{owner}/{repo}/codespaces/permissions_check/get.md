# Check if permissions defined by a devcontainer have been accepted by the authenticated user

`get /repos/{owner}/{repo}/codespaces/permissions_check`

Checks whether the permissions defined by a given devcontainer configuration have been accepted by the authenticated user.

OAuth app tokens and personal access tokens (classic) need the `codespace` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "Check if permissions defined by a devcontainer have been accepted by the authenticated user",
    "description": "Checks whether the permissions defined by a given devcontainer configuration have been accepted by the authenticated user.\n\nOAuth app tokens and personal access tokens (classic) need the `codespace` scope to use this endpoint.",
    "tags": [
        "codespaces"
    ],
    "operationId": "codespaces/check-permissions-for-devcontainer",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/codespaces/codespaces#check-if-permissions-defined-by-a-devcontainer-have-been-accepted-by-the-authenticated-user"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "name": "ref",
            "description": "The git reference that points to the location of the devcontainer configuration to use for the permission check. The value of `ref` will typically be a branch name (`heads/BRANCH_NAME`). For more information, see \"[Git References](https://git-scm.com/book/en/v2/Git-Internals-Git-References)\" in the Git documentation.",
            "in": "query",
            "required": true,
            "schema": {
                "type": "string",
                "example": "master"
            }
        },
        {
            "name": "devcontainer_path",
            "description": "Path to the devcontainer.json configuration to use for the permission check.",
            "in": "query",
            "required": true,
            "schema": {
                "type": "string",
                "example": ".devcontainer/example/devcontainer.json"
            }
        }
    ],
    "responses": {
        "200": {
            "description": "Response when the permission check is successful",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/codespaces-permissions-check-for-devcontainer"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/codespaces-permissions-check-for-devcontainer"
                        }
                    }
                }
            }
        },
        "401": {
            "$ref": "#/components/responses/requires_authentication"
        },
        "403": {
            "$ref": "#/components/responses/forbidden"
        },
        "404": {
            "$ref": "#/components/responses/not_found"
        },
        "422": {
            "$ref": "#/components/responses/validation_failed"
        },
        "503": {
            "$ref": "#/components/responses/service_unavailable"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "codespaces",
        "subcategory": "codespaces"
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

### `#/components/schemas/codespaces-permissions-check-for-devcontainer`

```json
{
    "title": "Codespaces Permissions Check",
    "description": "Permission check result for a given devcontainer config.",
    "type": "object",
    "properties": {
        "accepted": {
            "description": "Whether the user has accepted the permissions defined by the devcontainer config",
            "example": true,
            "type": "boolean"
        }
    },
    "required": [
        "accepted"
    ]
}
```

### `#/components/examples/codespaces-permissions-check-for-devcontainer`

```json
{
    "value": {
        "accepted": true
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

### `#/components/responses/service_unavailable`

```json
{
    "description": "Service unavailable",
    "content": {
        "application/json": {
            "schema": {
                "type": "object",
                "properties": {
                    "code": {
                        "type": "string"
                    },
                    "message": {
                        "type": "string"
                    },
                    "documentation_url": {
                        "type": "string"
                    }
                }
            }
        }
    }
}
```