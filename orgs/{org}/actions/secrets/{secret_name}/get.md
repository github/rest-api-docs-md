# Get an organization secret

Gets a single organization secret without revealing its encrypted value.

The authenticated user must have collaborator access to a repository to create, update, or read secrets

OAuth tokens and personal access tokens (classic) need the`admin:org` scope to use this endpoint. If the repository is private, OAuth tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "Get an organization secret",
    "description": "Gets a single organization secret without revealing its encrypted value.\n\nThe authenticated user must have collaborator access to a repository to create, update, or read secrets\n\nOAuth tokens and personal access tokens (classic) need the`admin:org` scope to use this endpoint. If the repository is private, OAuth tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.",
    "tags": [
        "actions"
    ],
    "operationId": "actions/get-org-secret",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/actions/secrets#get-an-organization-secret"
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
                        "$ref": "#/components/schemas/organization-actions-secret"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/organization-actions-secret"
                        }
                    }
                }
            }
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "actions",
        "subcategory": "secrets"
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

### `#/components/schemas/organization-actions-secret`

```json
{
    "title": "Actions Secret for an Organization",
    "description": "Secrets for GitHub Actions for an organization.",
    "type": "object",
    "properties": {
        "name": {
            "description": "The name of the secret.",
            "example": "SECRET_TOKEN",
            "type": "string"
        },
        "created_at": {
            "type": "string",
            "format": "date-time"
        },
        "updated_at": {
            "type": "string",
            "format": "date-time"
        },
        "visibility": {
            "description": "Visibility of a secret",
            "enum": [
                "all",
                "private",
                "selected"
            ],
            "type": "string"
        },
        "selected_repositories_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/organizations/org/secrets/my_secret/repositories"
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

### `#/components/examples/organization-actions-secret`

```json
{
    "value": {
        "name": "GH_TOKEN",
        "created_at": "2019-08-10T14:59:22Z",
        "updated_at": "2020-01-10T14:59:22Z",
        "visibility": "selected",
        "selected_repositories_url": "https://api.github.com/orgs/octo-org/actions/secrets/SUPER_SECRET/repositories"
    }
}
```