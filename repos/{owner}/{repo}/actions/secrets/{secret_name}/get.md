# Get a repository secret

`get /repos/{owner}/{repo}/actions/secrets/{secret_name}`

Gets a single repository secret without revealing its encrypted value.

The authenticated user must have collaborator access to the repository to use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "Get a repository secret",
    "description": "Gets a single repository secret without revealing its encrypted value.\n\nThe authenticated user must have collaborator access to the repository to use this endpoint.\n\nOAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.",
    "tags": [
        "actions"
    ],
    "operationId": "actions/get-repo-secret",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/actions/secrets#get-a-repository-secret"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
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
                        "$ref": "#/components/schemas/actions-secret"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/actions-secret"
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

### `#/components/schemas/actions-secret`

```json
{
    "title": "Actions Secret",
    "description": "Set secrets for GitHub Actions.",
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
        }
    },
    "required": [
        "name",
        "created_at",
        "updated_at"
    ]
}
```

### `#/components/examples/actions-secret`

```json
{
    "value": {
        "name": "GH_TOKEN",
        "created_at": "2019-08-10T14:59:22Z",
        "updated_at": "2020-01-10T14:59:22Z"
    }
}
```