# Get default code security configurations

`get /orgs/{org}/code-security/configurations/defaults`

Lists the default code security configurations for an organization.

The authenticated user must be an administrator or security manager for the organization to use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `write:org` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "Get default code security configurations",
    "description": "Lists the default code security configurations for an organization.\n\nThe authenticated user must be an administrator or security manager for the organization to use this endpoint.\n\nOAuth app tokens and personal access tokens (classic) need the `write:org` scope to use this endpoint.",
    "tags": [
        "code-security"
    ],
    "operationId": "code-security/get-default-configurations",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/code-security/configurations#get-default-code-security-configurations"
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
                        "$ref": "#/components/schemas/code-security-default-configurations"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/code-security-default-configurations"
                        }
                    }
                }
            }
        },
        "304": {
            "$ref": "#/components/responses/not_modified"
        },
        "403": {
            "$ref": "#/components/responses/forbidden"
        },
        "404": {
            "$ref": "#/components/responses/not_found"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "code-security",
        "subcategory": "configurations"
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

### `#/components/schemas/code-security-default-configurations`

```json
{
    "type": "array",
    "description": "A list of default code security configurations",
    "items": {
        "type": "object",
        "properties": {
            "default_for_new_repos": {
                "enum": [
                    "public",
                    "private_and_internal",
                    "all"
                ],
                "description": "The visibility of newly created repositories for which the code security configuration will be applied to by default"
            },
            "configuration": {
                "$ref": "#/components/schemas/code-security-configuration"
            }
        }
    }
}
```

### `#/components/examples/code-security-default-configurations`

```json
{
    "value": [
        {
            "default_for_new_repos": "public",
            "configuration": {
                "id": 1325,
                "target_type": "organization",
                "name": "octo-org recommended settings",
                "description": "This is a code security configuration for octo-org",
                "advanced_security": "enabled",
                "dependency_graph": "enabled",
                "dependabot_alerts": "enabled",
                "dependabot_security_updates": "not_set",
                "code_scanning_default_setup": "enabled",
                "secret_scanning": "enabled",
                "secret_scanning_push_protection": "enabled",
                "private_vulnerability_reporting": "enabled",
                "url": "https://api.github.com/orgs/octo-org/code-security/configurations/1325",
                "html_url": "https://github.com/organizations/octo-org/settings/security_products/configurations/edit/1325",
                "created_at": "2024-05-01T00:00:00Z",
                "updated_at": "2024-05-01T00:00:00Z"
            }
        },
        {
            "default_for_new_repos": "private_and_internal",
            "configuration": {
                "id": 17,
                "target_type": "global",
                "name": "GitHub recommended",
                "description": "Suggested settings for Dependabot, secret scanning, and code scanning.",
                "advanced_security": "enabled",
                "dependency_graph": "enabled",
                "dependabot_alerts": "enabled",
                "dependabot_security_updates": "not_set",
                "code_scanning_default_setup": "enabled",
                "secret_scanning": "enabled",
                "secret_scanning_push_protection": "enabled",
                "private_vulnerability_reporting": "enabled",
                "url": "https://api.github.com/orgs/octo-org/code-security/configurations/17",
                "html_url": "https://github.com/organizations/octo-org/settings/security_products/configurations/view",
                "created_at": "2023-12-04T15:58:07Z",
                "updated_at": "2023-12-04T15:58:07Z"
            }
        }
    ]
}
```

### `#/components/responses/not_modified`

```json
{
    "description": "Not modified"
}
```

### `#/components/responses/forbidden`

```json
{
    "description": "Forbidden",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/basic-error"
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