# Get the customization template for an OIDC subject claim for a repository

Gets the customization template for an OpenID Connect (OIDC) subject claim.

OAuth tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "Get the customization template for an OIDC subject claim for a repository",
    "description": "Gets the customization template for an OpenID Connect (OIDC) subject claim.\n\nOAuth tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.",
    "tags": [
        "actions"
    ],
    "operationId": "actions/get-custom-oidc-sub-claim-for-repo",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/actions/oidc#get-the-customization-template-for-an-oidc-subject-claim-for-a-repository"
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
            "description": "Status response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/oidc-custom-sub-repo"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/oidc-custom-sub-repo"
                        }
                    }
                }
            }
        },
        "400": {
            "$ref": "#/components/responses/bad_request"
        },
        "404": {
            "$ref": "#/components/responses/not_found"
        }
    },
    "x-github": {
        "enabledForGitHubApps": true,
        "previews": [],
        "category": "actions",
        "subcategory": "oidc"
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

### `#/components/schemas/oidc-custom-sub-repo`

```json
{
    "title": "Actions OIDC subject customization for a repository",
    "description": "Actions OIDC subject customization for a repository",
    "type": "object",
    "properties": {
        "use_default": {
            "description": "Whether to use the default template or not. If `true`, the `include_claim_keys` field is ignored.",
            "type": "boolean"
        },
        "include_claim_keys": {
            "description": "Array of unique strings. Each claim key can only contain alphanumeric characters and underscores.",
            "type": "array",
            "items": {
                "type": "string"
            }
        }
    },
    "required": [
        "use_default"
    ]
}
```

### `#/components/examples/oidc-custom-sub-repo`

```json
{
    "value": {
        "use_default": false,
        "include_claim_keys": [
            "repo",
            "context"
        ]
    }
}
```

### `#/components/responses/bad_request`

```json
{
    "description": "Bad Request",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/basic-error"
            }
        },
        "application/scim+json": {
            "schema": {
                "$ref": "#/components/schemas/scim-error"
            }
        }
    }
}
```

### `#/components/responses/not_found`

```json
{
    "description": "Resource not found",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/basic-error"
            }
        }
    }
}
```