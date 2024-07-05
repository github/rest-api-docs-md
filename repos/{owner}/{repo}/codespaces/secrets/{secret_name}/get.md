# Get a repository secret

`get /repos/{owner}/{repo}/codespaces/secrets/{secret_name}`

Gets a single repository development environment secret without revealing its encrypted value.

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "Get a repository secret",
    "description": "Gets a single repository development environment secret without revealing its encrypted value.\n\nOAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.",
    "tags": [
        "codespaces"
    ],
    "operationId": "codespaces/get-repo-secret",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/codespaces/repository-secrets#get-a-repository-secret"
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
                        "$ref": "#/components/schemas/repo-codespaces-secret"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/repo-codespaces-secret"
                        }
                    }
                }
            }
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "codespaces",
        "subcategory": "repository-secrets"
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

### `#/components/schemas/repo-codespaces-secret`

```json
{
    "title": "Codespaces Secret",
    "description": "Set repository secrets for GitHub Codespaces.",
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