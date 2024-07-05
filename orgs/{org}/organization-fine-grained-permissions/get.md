# List organization fine-grained permissions for an organization

Lists the fine-grained permissions that can be used in custom organization roles for an organization. For more information, see "[Managing people's access to your organization with roles](https://docs.github.com/organizations/managing-peoples-access-to-your-organization-with-roles/about-custom-organization-roles)."

To list the fine-grained permissions that can be used in custom repository roles for an organization, see "[List repository fine-grained permissions for an organization](https://docs.github.com/rest/orgs/organization-roles#list-repository-fine-grained-permissions-for-an-organization)."

To use this endpoint, the authenticated user must be one of:

- An administrator for the organization.
- A user, or a user on a team, with the fine-grained permissions of `read_organization_custom_org_role` in the organization.

OAuth app tokens and personal access tokens (classic) need the `admin:org` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "List organization fine-grained permissions for an organization",
    "description": "Lists the fine-grained permissions that can be used in custom organization roles for an organization. For more information, see \"[Managing people's access to your organization with roles](https://docs.github.com/organizations/managing-peoples-access-to-your-organization-with-roles/about-custom-organization-roles).\"\n\nTo list the fine-grained permissions that can be used in custom repository roles for an organization, see \"[List repository fine-grained permissions for an organization](https://docs.github.com/rest/orgs/organization-roles#list-repository-fine-grained-permissions-for-an-organization).\"\n\nTo use this endpoint, the authenticated user must be one of:\n\n- An administrator for the organization.\n- A user, or a user on a team, with the fine-grained permissions of `read_organization_custom_org_role` in the organization.\n\nOAuth app tokens and personal access tokens (classic) need the `admin:org` scope to use this endpoint.",
    "tags": [
        "orgs"
    ],
    "operationId": "orgs/list-organization-fine-grained-permissions",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/orgs/organization-roles#list-organization-fine-grained-permissions-for-an-organization"
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
                        "type": "array",
                        "items": {
                            "$ref": "#/components/schemas/organization-fine-grained-permission"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/organization-fine-grained-permission-example"
                        }
                    }
                }
            }
        },
        "404": {
            "$ref": "#/components/responses/not_found"
        },
        "422": {
            "$ref": "#/components/responses/validation_failed"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "orgs",
        "subcategory": "organization-roles"
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

### `#/components/schemas/organization-fine-grained-permission`

```json
{
    "title": "Organization Fine-Grained Permission",
    "description": "A fine-grained permission that protects organization resources.",
    "type": "object",
    "properties": {
        "name": {
            "type": "string"
        },
        "description": {
            "type": "string"
        }
    },
    "required": [
        "name",
        "description"
    ]
}
```

### `#/components/examples/organization-fine-grained-permission-example`

```json
{
    "value": [
        {
            "name": "read_organization_custom_org_role",
            "description": "View organization roles"
        },
        {
            "name": "write_organization_custom_org_role",
            "description": "Manage custom organization roles"
        }
    ]
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

### `#/components/responses/validation_failed`

```json
{
    "description": "Validation failed, or the endpoint has been spammed.",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/validation-error"
            }
        }
    }
}
```