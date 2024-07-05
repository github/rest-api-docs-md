# Get an organization public key

`get /orgs/{org}/codespaces/secrets/public-key`

Gets a public key for an organization, which is required in order to encrypt secrets. You need to encrypt the value of a secret before you can create or update secrets.
OAuth app tokens and personal access tokens (classic) need the `admin:org` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "Get an organization public key",
    "description": "Gets a public key for an organization, which is required in order to encrypt secrets. You need to encrypt the value of a secret before you can create or update secrets.\nOAuth app tokens and personal access tokens (classic) need the `admin:org` scope to use this endpoint.",
    "tags": [
        "codespaces"
    ],
    "operationId": "codespaces/get-org-public-key",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/codespaces/organization-secrets#get-an-organization-public-key"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/org"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/codespaces-public-key"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/codespaces-public-key"
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

### `#/components/schemas/codespaces-public-key`

```json
{
    "title": "CodespacesPublicKey",
    "description": "The public key used for setting Codespaces secrets.",
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

### `#/components/examples/codespaces-public-key`

```json
{
    "value": {
        "key_id": "012345678912345678",
        "key": "2Sg8iYjAxxmI2LvUXpJjkYrMxURPc8r+dB7TJyvv1234"
    }
}
```