# Get an organization role

`get /orgs/{org}/organization-roles/{role_id}`

Gets an organization role that is available to this organization. For more information on organization roles, see "[Managing people's access to your organization with roles](https://docs.github.com/organizations/managing-peoples-access-to-your-organization-with-roles/about-custom-organization-roles)."

To use this endpoint, the authenticated user must be one of:

- An administrator for the organization.
- A user, or a user on a team, with the fine-grained permissions of `read_organization_custom_org_role` in the organization.

OAuth app tokens and personal access tokens (classic) need the `admin:org` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "Get an organization role",
    "description": "Gets an organization role that is available to this organization. For more information on organization roles, see \"[Managing people's access to your organization with roles](https://docs.github.com/organizations/managing-peoples-access-to-your-organization-with-roles/about-custom-organization-roles).\"\n\nTo use this endpoint, the authenticated user must be one of:\n\n- An administrator for the organization.\n- A user, or a user on a team, with the fine-grained permissions of `read_organization_custom_org_role` in the organization.\n\nOAuth app tokens and personal access tokens (classic) need the `admin:org` scope to use this endpoint.",
    "tags": [
        "orgs"
    ],
    "operationId": "orgs/get-org-role",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/orgs/organization-roles#get-an-organization-role"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/org"
        },
        {
            "$ref": "#/components/parameters/role-id"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/organization-role"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/organization-role"
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

### `#/components/parameters/role-id`

```json
{
    "name": "role_id",
    "description": "The unique identifier of the role.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "integer"
    }
}
```

### `#/components/schemas/organization-role`

```json
{
    "title": "Organization Role",
    "description": "Organization roles",
    "type": "object",
    "properties": {
        "id": {
            "description": "The unique identifier of the role.",
            "type": "integer",
            "format": "int64"
        },
        "name": {
            "description": "The name of the role.",
            "type": "string"
        },
        "description": {
            "description": "A short description about who this role is for or what permissions it grants.",
            "type": "string",
            "nullable": true
        },
        "permissions": {
            "description": "A list of permissions included in this role.",
            "type": "array",
            "items": {
                "type": "string"
            }
        },
        "organization": {
            "$ref": "#/components/schemas/nullable-simple-user"
        },
        "created_at": {
            "description": "The date and time the role was created.",
            "type": "string",
            "format": "date-time"
        },
        "updated_at": {
            "description": "The date and time the role was last updated.",
            "type": "string",
            "format": "date-time"
        }
    },
    "required": [
        "id",
        "name",
        "permissions",
        "organization",
        "created_at",
        "updated_at"
    ]
}
```

### `#/components/examples/organization-role`

```json
{
    "value": {
        "id": 8030,
        "name": "Custom Role Manager",
        "description": "Permissions to manage custom roles within an org",
        "permissions": [
            "write_organization_custom_repo_role",
            "write_organization_custom_org_role",
            "read_organization_custom_repo_role",
            "read_organization_custom_org_role"
        ],
        "organization": {
            "login": "github",
            "id": 1,
            "node_id": "MDEyOk9yZ2FuaXphdGlvbjE=",
            "url": "https://api.github.com/orgs/github",
            "repos_url": "https://api.github.com/orgs/github/repos",
            "events_url": "https://api.github.com/orgs/github/events",
            "hooks_url": "https://api.github.com/orgs/github/hooks",
            "issues_url": "https://api.github.com/orgs/github/issues",
            "members_url": "https://api.github.com/orgs/github/members{/member}",
            "public_members_url": "https://api.github.com/orgs/github/public_members{/member}",
            "avatar_url": "https://github.com/images/error/octocat_happy.gif",
            "description": "A great organization"
        },
        "created_at": "2022-07-04T22:19:11Z",
        "updated_at": "2022-07-04T22:20:11Z"
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