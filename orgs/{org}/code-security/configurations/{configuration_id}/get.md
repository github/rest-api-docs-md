# Get a code security configuration

`get /orgs/{org}/code-security/configurations/{configuration_id}`

Gets a code security configuration available in an organization.

The authenticated user must be an administrator or security manager for the organization to use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `write:org` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "Get a code security configuration",
    "description": "Gets a code security configuration available in an organization.\n\nThe authenticated user must be an administrator or security manager for the organization to use this endpoint.\n\nOAuth app tokens and personal access tokens (classic) need the `write:org` scope to use this endpoint.",
    "tags": [
        "code-security"
    ],
    "operationId": "code-security/get-configuration",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/code-security/configurations#get-a-code-security-configuration"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/org"
        },
        {
            "$ref": "#/components/parameters/configuration-id"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/code-security-configuration"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/code-security-configuration"
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

### `#/components/parameters/configuration-id`

```json
{
    "name": "configuration_id",
    "description": "The unique identifier of the code security configuration.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "integer"
    }
}
```

### `#/components/schemas/code-security-configuration`

```json
{
    "type": "object",
    "description": "A code security configuration",
    "properties": {
        "id": {
            "type": "integer",
            "description": "The ID of the code security configuration"
        },
        "name": {
            "type": "string",
            "description": "The name of the code security configuration. Must be unique within the organization."
        },
        "target_type": {
            "type": "string",
            "description": "The type of the code security configuration.",
            "enum": [
                "global",
                "organization"
            ]
        },
        "description": {
            "type": "string",
            "description": "A description of the code security configuration"
        },
        "advanced_security": {
            "type": "string",
            "description": "The enablement status of GitHub Advanced Security",
            "enum": [
                "enabled",
                "disabled"
            ]
        },
        "dependency_graph": {
            "type": "string",
            "description": "The enablement status of Dependency Graph",
            "enum": [
                "enabled",
                "disabled",
                "not_set"
            ]
        },
        "dependabot_alerts": {
            "type": "string",
            "description": "The enablement status of Dependabot alerts",
            "enum": [
                "enabled",
                "disabled",
                "not_set"
            ]
        },
        "dependabot_security_updates": {
            "type": "string",
            "description": "The enablement status of Dependabot security updates",
            "enum": [
                "enabled",
                "disabled",
                "not_set"
            ]
        },
        "code_scanning_default_setup": {
            "type": "string",
            "description": "The enablement status of code scanning default setup",
            "enum": [
                "enabled",
                "disabled",
                "not_set"
            ]
        },
        "secret_scanning": {
            "type": "string",
            "description": "The enablement status of secret scanning",
            "enum": [
                "enabled",
                "disabled",
                "not_set"
            ]
        },
        "secret_scanning_push_protection": {
            "type": "string",
            "description": "The enablement status of secret scanning push protection",
            "enum": [
                "enabled",
                "disabled",
                "not_set"
            ]
        },
        "private_vulnerability_reporting": {
            "type": "string",
            "description": "The enablement status of private vulnerability reporting",
            "enum": [
                "enabled",
                "disabled",
                "not_set"
            ]
        },
        "url": {
            "type": "string",
            "format": "uri",
            "description": "The URL of the configuration"
        },
        "html_url": {
            "type": "string",
            "format": "uri",
            "description": "The URL of the configuration"
        },
        "created_at": {
            "type": "string",
            "format": "date-time"
        },
        "updated_at": {
            "type": "string",
            "format": "date-time"
        }
    }
}
```

### `#/components/examples/code-security-configuration`

```json
{
    "value": {
        "id": 1325,
        "target_type": "organization",
        "name": "octo-org recommended settings",
        "description": "This is a code security configuration for octo-org",
        "advanced_security": "enabled",
        "dependency_graph": "enabled",
        "dependabot_alerts": "enabled",
        "dependabot_security_updates": "not_set",
        "code_scanning_default_setup": "disabled",
        "secret_scanning": "enabled",
        "secret_scanning_push_protection": "disabled",
        "private_vulnerability_reporting": "disabled",
        "url": "https://api.github.com/orgs/octo-org/code-security/configurations/1325",
        "html_url": "https://github.com/organizations/octo-org/settings/security_products/configurations/edit/1325",
        "created_at": "2024-05-01T00:00:00Z",
        "updated_at": "2024-05-01T00:00:00Z"
    }
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