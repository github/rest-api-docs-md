# Get an environment public key

Get the public key for an environment, which you need to encrypt environment
secrets. You need to encrypt a secret before you can create or update secrets.

Anyone with read access to the repository can use this endpoint.

If the repository is private, OAuth tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "Get an environment public key",
    "description": "Get the public key for an environment, which you need to encrypt environment\nsecrets. You need to encrypt a secret before you can create or update secrets.\n\nAnyone with read access to the repository can use this endpoint.\n\nIf the repository is private, OAuth tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.",
    "tags": [
        "actions"
    ],
    "operationId": "actions/get-environment-public-key",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/actions/secrets#get-an-environment-public-key"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "$ref": "#/components/parameters/environment-name"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/actions-public-key"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/actions-public-key"
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

### `#/components/parameters/environment-name`

```json
{
    "name": "environment_name",
    "in": "path",
    "required": true,
    "description": "The name of the environment. The name must be URL encoded. For example, any slashes in the name must be replaced with `%2F`.",
    "schema": {
        "type": "string"
    }
}
```

### `#/components/schemas/actions-public-key`

```json
{
    "title": "ActionsPublicKey",
    "description": "The public key used for setting Actions Secrets.",
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
        },
        "id": {
            "type": "integer",
            "example": 2
        },
        "url": {
            "type": "string",
            "example": "https://api.github.com/user/keys/2"
        },
        "title": {
            "type": "string",
            "example": "ssh-rsa AAAAB3NzaC1yc2EAAA"
        },
        "created_at": {
            "type": "string",
            "example": "2011-01-26T19:01:12Z"
        }
    },
    "required": [
        "key_id",
        "key"
    ]
}
```

### `#/components/examples/actions-public-key`

```json
{
    "value": {
        "key_id": "012345678912345678",
        "key": "2Sg8iYjAxxmI2LvUXpJjkYrMxURPc8r+dB7TJyvv1234"
    }
}
```