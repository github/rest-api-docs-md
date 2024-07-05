# Get an organization secret

Gets an organization development environment secret without revealing its encrypted value.

OAuth app tokens and personal access tokens (classic) need the `admin:org` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "Get an organization secret",
    "description": "Gets an organization development environment secret without revealing its encrypted value.\n\nOAuth app tokens and personal access tokens (classic) need the `admin:org` scope to use this endpoint.",
    "tags": [
        "codespaces"
    ],
    "operationId": "codespaces/get-org-secret",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/codespaces/organization-secrets#get-an-organization-secret"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/org"
        },
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
                        "$ref": "#/components/schemas/codespaces-org-secret"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/repo-codespaces-secret"
                        }
                    }
                }
            },
            "headers": {
                "Link": {
                    "$ref": "#/components/headers/link"
                }
            }
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": false,
        "category": "codespaces",
        "subcategory": "organization-secrets"
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

### `#/components/schemas/codespaces-org-secret`

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
            "description": "The date and time at which the secret was created, in ISO 8601 format':' YYYY-MM-DDTHH:MM:SSZ.",
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
            "example": "https://api.github.com/orgs/ORGANIZATION/codespaces/secrets/SECRET_NAME/repositories"
        }
    },
    "required": [
        "name",
        "created_at",
        "updated_at",
        "visibility"
    ]
}
```

### `#/components/examples/repo-codespaces-secret`

```json
{
    "value": {
        "name": "GH_TOKEN",
        "created_at": "2019-08-10T14:59:22Z",
        "updated_at": "2020-01-10T14:59:22Z",
        "visibility": "all"
    }
}
```

### `#/components/headers/link`

```json
{
    "example": "<https://api.github.com/resource?page=2>; rel=\"next\", <https://api.github.com/resource?page=5>; rel=\"last\"",
    "schema": {
        "type": "string"
    }
}
```