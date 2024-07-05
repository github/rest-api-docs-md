# Get the customization template for an OIDC subject claim for an organization

Gets the customization template for an OpenID Connect (OIDC) subject claim.

OAuth app tokens and personal access tokens (classic) need the `read:org` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "Get the customization template for an OIDC subject claim for an organization",
    "description": "Gets the customization template for an OpenID Connect (OIDC) subject claim.\n\nOAuth app tokens and personal access tokens (classic) need the `read:org` scope to use this endpoint.",
    "tags": [
        "oidc"
    ],
    "operationId": "oidc/get-oidc-custom-sub-template-for-org",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/actions/oidc#get-the-customization-template-for-an-oidc-subject-claim-for-an-organization"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/org"
        }
    ],
    "responses": {
        "200": {
            "description": "A JSON serialized template for OIDC subject claim customization",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/oidc-custom-sub"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/oidc-custom-sub"
                        }
                    }
                }
            }
        }
    },
    "x-github": {
        "enabledForGitHubApps": true,
        "category": "actions",
        "subcategory": "oidc"
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

### `#/components/schemas/oidc-custom-sub`

```json
{
    "title": "Actions OIDC Subject customization",
    "description": "Actions OIDC Subject customization",
    "type": "object",
    "properties": {
        "include_claim_keys": {
            "description": "Array of unique strings. Each claim key can only contain alphanumeric characters and underscores.",
            "type": "array",
            "items": {
                "type": "string"
            }
        }
    },
    "required": [
        "include_claim_keys"
    ]
}
```

### `#/components/examples/oidc-custom-sub`

```json
{
    "value": {
        "include_claim_keys": [
            "repo",
            "context"
        ]
    }
}
```