# Get GitHub Actions permissions for a repository

Gets the GitHub Actions permissions policy for a repository, including whether GitHub Actions is enabled and the actions and reusable workflows allowed to run in the repository.

OAuth tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "Get GitHub Actions permissions for a repository",
    "description": "Gets the GitHub Actions permissions policy for a repository, including whether GitHub Actions is enabled and the actions and reusable workflows allowed to run in the repository.\n\nOAuth tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.",
    "operationId": "actions/get-github-actions-permissions-repository",
    "tags": [
        "actions"
    ],
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/actions/permissions#get-github-actions-permissions-for-a-repository"
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
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/actions-repository-permissions"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/actions-repository-permissions"
                        }
                    }
                }
            }
        }
    },
    "x-github": {
        "enabledForGitHubApps": true,
        "githubCloudOnly": false,
        "category": "actions",
        "subcategory": "permissions"
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

### `#/components/schemas/actions-repository-permissions`

```json
{
    "type": "object",
    "properties": {
        "enabled": {
            "$ref": "#/components/schemas/actions-enabled"
        },
        "allowed_actions": {
            "$ref": "#/components/schemas/allowed-actions"
        },
        "selected_actions_url": {
            "$ref": "#/components/schemas/selected-actions-url"
        }
    },
    "required": [
        "enabled"
    ]
}
```

### `#/components/examples/actions-repository-permissions`

```json
{
    "value": {
        "enabled": true,
        "allowed_actions": "selected",
        "selected_actions_url": "https://api.github.com/repositories/42/actions/permissions/selected-actions"
    }
}
```