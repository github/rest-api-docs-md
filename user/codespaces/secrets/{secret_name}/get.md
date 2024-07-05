# Get a secret for the authenticated user

Gets a development environment secret available to a user's codespaces without revealing its encrypted value.

The authenticated user must have Codespaces access to use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `codespace` or `codespace:secrets` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "Get a secret for the authenticated user",
    "description": "Gets a development environment secret available to a user's codespaces without revealing its encrypted value.\n\nThe authenticated user must have Codespaces access to use this endpoint.\n\nOAuth app tokens and personal access tokens (classic) need the `codespace` or `codespace:secrets` scope to use this endpoint.",
    "tags": [
        "codespaces"
    ],
    "operationId": "codespaces/get-secret-for-authenticated-user",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/codespaces/secrets#get-a-secret-for-the-authenticated-user"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/secret-name"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/codespaces-secret"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/user-codespaces-secret"
                        }
                    }
                }
            }
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": false,
        "category": "codespaces",
        "subcategory": "secrets"
    }
}
```

## References

### `#/components/parameters/secret-name`

```json
{
    "name": "secret_name",
    "description": "The name of the secret.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "string"
    }
}
```

### `#/components/schemas/codespaces-secret`

```json
{
    "title": "Codespaces Secret",
    "description": "Secrets for a GitHub Codespace.",
    "type": "object",
    "properties": {
        "name": {
            "description": "The name of the secret",
            "example": "SECRET_NAME",
            "type": "string"
        },
        "created_at": {
            "description": "The date and time at which the secret was created, in ISO 8601 format':' YYYY-MM-DDTHH:MM:SSZ.",
            "type": "string",
            "format": "date-time"
        },
        "updated_at": {
            "description": "The date and time at which the secret was last updated, in ISO 8601 format':' YYYY-MM-DDTHH:MM:SSZ.",
            "type": "string",
            "format": "date-time"
        },
        "visibility": {
            "description": "The type of repositories in the organization that the secret is visible to",
            "enum": [
                "all",
                "private",
                "selected"
            ],
            "type": "string"
        },
        "selected_repositories_url": {
            "description": "The API URL at which the list of repositories this secret is visible to can be retrieved",
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/user/secrets/SECRET_NAME/repositories"
        }
    },
    "required": [
        "name",
        "created_at",
        "updated_at",
        "visibility",
        "selected_repositories_url"
    ]
}
```

### `#/components/examples/user-codespaces-secret`

```json
{
    "value": {
        "name": "CODESPACE_GH_SECRET",
        "created_at": "2019-08-10T14:59:22Z",
        "updated_at": "2020-01-10T14:59:22Z",
        "visibility": "selected",
        "selected_repositories_url": "https://api.github.com/user/codespaces/secrets/CODESPACE_GH_SECRET/repositories"
    }
}
```