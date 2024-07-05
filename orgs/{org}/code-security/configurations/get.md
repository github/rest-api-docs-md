# Get code security configurations for an organization

`get /orgs/{org}/code-security/configurations`

Lists all code security configurations available in an organization.

The authenticated user must be an administrator or security manager for the organization to use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `write:org` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "Get code security configurations for an organization",
    "description": "Lists all code security configurations available in an organization.\n\nThe authenticated user must be an administrator or security manager for the organization to use this endpoint.\n\nOAuth app tokens and personal access tokens (classic) need the `write:org` scope to use this endpoint.",
    "tags": [
        "code-security"
    ],
    "operationId": "code-security/get-configurations-for-org",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/code-security/configurations#get-code-security-configurations-for-an-organization"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/org"
        },
        {
            "name": "target_type",
            "in": "query",
            "description": "The target type of the code security configuration",
            "required": false,
            "schema": {
                "type": "string",
                "enum": [
                    "global",
                    "all"
                ],
                "default": "all"
            }
        },
        {
            "name": "per_page",
            "in": "query",
            "description": "'The number of results per page (max 100). For more information, see \"[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api).\"'\n",
            "required": false,
            "schema": {
                "type": "integer",
                "default": 30
            }
        },
        {
            "$ref": "#/components/parameters/pagination-before"
        },
        {
            "$ref": "#/components/parameters/pagination-after"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "type": "array",
                        "items": {
                            "$ref": "#/components/schemas/code-security-configuration"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/code-security-configuration-list"
                        }
                    }
                }
            }
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

### `#/components/parameters/pagination-before`

```json
{
    "name": "before",
    "description": "A cursor, as given in the [Link header](https://docs.github.com/rest/guides/using-pagination-in-the-rest-api#using-link-headers). If specified, the query only searches for results before this cursor. For more information, see \"[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api).\"",
    "in": "query",
    "required": false,
    "schema": {
        "type": "string"
    }
}
```

### `#/components/parameters/pagination-after`

```json
{
    "name": "after",
    "description": "A cursor, as given in the [Link header](https://docs.github.com/rest/guides/using-pagination-in-the-rest-api#using-link-headers). If specified, the query only searches for results after this cursor. For more information, see \"[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api).\"",
    "in": "query",
    "required": false,
    "schema": {
        "type": "string"
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

### `#/components/examples/code-security-configuration-list`

```json
{
    "value": [
        {
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
        },
        {
            "id": 1326,
            "target_type": "organization",
            "name": "High risk settings",
            "description": "This is a code security configuration for octo-org high risk repositories",
            "advanced_security": "enabled",
            "dependency_graph": "enabled",
            "dependabot_alerts": "enabled",
            "dependabot_security_updates": "enabled",
            "code_scanning_default_setup": "enabled",
            "secret_scanning": "enabled",
            "secret_scanning_push_protection": "enabled",
            "private_vulnerability_reporting": "enabled",
            "url": "https://api.github.com/orgs/octo-org/code-security/configurations/1326",
            "html_url": "https://github.com/organizations/octo-org/settings/security_products/configurations/edit/1326",
            "created_at": "2024-05-10T00:00:00Z",
            "updated_at": "2024-05-10T00:00:00Z"
        }
    ]
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