# Get public key for the authenticated user

Gets your public key, which you need to encrypt secrets. You need to encrypt a secret before you can create or update secrets.

The authenticated user must have Codespaces access to use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `codespace` or `codespace:secrets` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "Get public key for the authenticated user",
    "description": "Gets your public key, which you need to encrypt secrets. You need to encrypt a secret before you can create or update secrets.\n\nThe authenticated user must have Codespaces access to use this endpoint.\n\nOAuth app tokens and personal access tokens (classic) need the `codespace` or `codespace:secrets` scope to use this endpoint.",
    "tags": [
        "codespaces"
    ],
    "operationId": "codespaces/get-public-key-for-authenticated-user",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/codespaces/secrets#get-public-key-for-the-authenticated-user"
    },
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/codespaces-user-public-key"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/codespaces-user-public-key"
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

### `#/components/schemas/codespaces-user-public-key`

```json
{
    "title": "CodespacesUserPublicKey",
    "description": "The public key used for setting user Codespaces' Secrets.",
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

### `#/components/examples/codespaces-user-public-key`

```json
{
    "value": {
        "key_id": "012345678912345678",
        "key": "2Sg8iYjAxxmI2LvUXpJjkYrMxURPc8r+dB7TJyvv1234"
    }
}
```