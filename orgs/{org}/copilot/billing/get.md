# Get Copilot seat information and settings for an organization

**Note**: This endpoint is in beta and is subject to change.

Gets information about an organization's Copilot subscription, including seat breakdown
and feature policies. To configure these settings, go to your organization's settings on GitHub.com.
For more information, see "[Managing policies for Copilot in your organization](https://docs.github.com/copilot/managing-copilot/managing-policies-for-copilot-business-in-your-organization)".

Only organization owners can view details about the organization's Copilot Business or Copilot Enterprise subscription.

OAuth app tokens and personal access tokens (classic) need either the `manage_billing:copilot` or `read:org` scopes to use this endpoint.

## Operation Object

```json
{
    "summary": "Get Copilot seat information and settings for an organization",
    "description": "**Note**: This endpoint is in beta and is subject to change.\n\nGets information about an organization's Copilot subscription, including seat breakdown\nand feature policies. To configure these settings, go to your organization's settings on GitHub.com.\nFor more information, see \"[Managing policies for Copilot in your organization](https://docs.github.com/copilot/managing-copilot/managing-policies-for-copilot-business-in-your-organization)\".\n\nOnly organization owners can view details about the organization's Copilot Business or Copilot Enterprise subscription.\n\nOAuth app tokens and personal access tokens (classic) need either the `manage_billing:copilot` or `read:org` scopes to use this endpoint.",
    "tags": [
        "copilot"
    ],
    "operationId": "copilot/get-copilot-organization-details",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/copilot/copilot-user-management#get-copilot-seat-information-and-settings-for-an-organization"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/org"
        }
    ],
    "responses": {
        "200": {
            "description": "OK",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/copilot-organization-details"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/copilot-organization-details"
                        }
                    }
                }
            }
        },
        "500": {
            "$ref": "#/components/responses/internal_error"
        },
        "401": {
            "$ref": "#/components/responses/requires_authentication"
        },
        "403": {
            "$ref": "#/components/responses/forbidden"
        },
        "404": {
            "$ref": "#/components/responses/not_found"
        },
        "422": {
            "description": "There is a problem with your account's associated payment method."
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "copilot",
        "subcategory": "copilot-user-management"
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

### `#/components/schemas/copilot-organization-details`

```json
{
    "title": "Copilot Business Organization Details",
    "description": "Information about the seat breakdown and policies set for an organization with a Copilot Business subscription.",
    "type": "object",
    "properties": {
        "seat_breakdown": {
            "$ref": "#/components/schemas/copilot-seat-breakdown"
        },
        "public_code_suggestions": {
            "type": "string",
            "description": "The organization policy for allowing or disallowing Copilot to make suggestions that match public code.",
            "enum": [
                "allow",
                "block",
                "unconfigured",
                "unknown"
            ]
        },
        "ide_chat": {
            "type": "string",
            "description": "The organization policy for allowing or disallowing organization members to use Copilot Chat within their editor.",
            "enum": [
                "enabled",
                "disabled",
                "unconfigured"
            ]
        },
        "platform_chat": {
            "type": "string",
            "description": "The organization policy for allowing or disallowing organization members to use Copilot features within github.com.",
            "enum": [
                "enabled",
                "disabled",
                "unconfigured"
            ]
        },
        "cli": {
            "type": "string",
            "description": "The organization policy for allowing or disallowing organization members to use Copilot within their CLI.",
            "enum": [
                "enabled",
                "disabled",
                "unconfigured"
            ]
        },
        "seat_management_setting": {
            "type": "string",
            "description": "The mode of assigning new seats.",
            "enum": [
                "assign_all",
                "assign_selected",
                "disabled",
                "unconfigured"
            ]
        }
    },
    "required": [
        "seat_breakdown",
        "public_code_suggestions",
        "seat_management_setting"
    ],
    "additionalProperties": true
}
```

### `#/components/examples/copilot-organization-details`

```json
{
    "value": {
        "seat_breakdown": {
            "total": 12,
            "added_this_cycle": 9,
            "pending_invitation": 0,
            "pending_cancellation": 0,
            "active_this_cycle": 12,
            "inactive_this_cycle": 11
        },
        "seat_management_setting": "assign_selected",
        "public_code_suggestions": "block"
    }
}
```

### `#/components/responses/internal_error`

```json
{
    "description": "Internal Error",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/basic-error"
            }
        }
    }
}
```

### `#/components/responses/requires_authentication`

```json
{
    "description": "Requires authentication",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/basic-error"
            }
        }
    }
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