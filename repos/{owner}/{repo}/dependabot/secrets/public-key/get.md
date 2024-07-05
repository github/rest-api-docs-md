# Get a repository public key

Gets your public key, which you need to encrypt secrets. You need to
encrypt a secret before you can create or update secrets. Anyone with read access
to the repository can use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint if the repository is private.

## Operation Object

```json
{
    "summary": "Get a repository public key",
    "description": "Gets your public key, which you need to encrypt secrets. You need to\nencrypt a secret before you can create or update secrets. Anyone with read access\nto the repository can use this endpoint.\n\nOAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint if the repository is private.",
    "tags": [
        "dependabot"
    ],
    "operationId": "dependabot/get-repo-public-key",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/dependabot/secrets#get-a-repository-public-key"
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
                        "$ref": "#/components/schemas/dependabot-public-key"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/dependabot-public-key"
                        }
                    }
                }
            }
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "dependabot",
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

### `#/components/schemas/dependabot-public-key`

```json
{
    "title": "DependabotPublicKey",
    "description": "The public key used for setting Dependabot Secrets.",
    "type": "object",
    "properties": {
        "key_id": {
            "description": "The identifier for the key.",
            "type": "string",
            "example": "1234567"
        },
        "key": {
            "description": "The Base64 encoded public key.",
            "type": "string",
            "example": "hBT5WZEj8ZoOv6TYJsfWq7MxTEQopZO5/IT3ZCVQPzs="
        }
    },
    "required": [
        "key_id",
        "key"
    ]
}
```

### `#/components/examples/dependabot-public-key`

```json
{
    "value": {
        "key_id": "012345678912345678",
        "key": "2Sg8iYjAxxmI2LvUXpJjkYrMxURPc8r+dB7TJyvv1234"
    }
}
```