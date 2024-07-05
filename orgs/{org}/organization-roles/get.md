# Get all organization roles for an organization

`get /orgs/{org}/organization-roles`

Lists the organization roles available in this organization. For more information on organization roles, see "[Managing people's access to your organization with roles](https://docs.github.com/organizations/managing-peoples-access-to-your-organization-with-roles/about-custom-organization-roles)."

To use this endpoint, the authenticated user must be one of:

- An administrator for the organization.
- A user, or a user on a team, with the fine-grained permissions of `read_organization_custom_org_role` in the organization.

OAuth app tokens and personal access tokens (classic) need the `admin:org` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "Get all organization roles for an organization",
    "description": "Lists the organization roles available in this organization. For more information on organization roles, see \"[Managing people's access to your organization with roles](https://docs.github.com/organizations/managing-peoples-access-to-your-organization-with-roles/about-custom-organization-roles).\"\n\nTo use this endpoint, the authenticated user must be one of:\n\n- An administrator for the organization.\n- A user, or a user on a team, with the fine-grained permissions of `read_organization_custom_org_role` in the organization.\n\nOAuth app tokens and personal access tokens (classic) need the `admin:org` scope to use this endpoint.",
    "tags": [
        "orgs"
    ],
    "operationId": "orgs/list-org-roles",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/orgs/organization-roles#get-all-organization-roles-for-an-organization"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/org"
        }
    ],
    "responses": {
        "200": {
            "description": "Response - list of organization roles",
            "content": {
                "application/json": {
                    "schema": {
                        "type": "object",
                        "properties": {
                            "total_count": {
                                "type": "integer",
                                "description": "The total number of organization roles available to the organization."
                            },
                            "roles": {
                                "type": "array",
                                "description": "The list of organization roles available to the organization.",
                                "items": {
                                    "$ref": "#/components/schemas/organization-role"
                                }
                            }
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/organization-role-list"
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

### `#/components/examples/organization-role-list`

```json
{
    "value": {
        "total_count": 2,
        "roles": [
            {
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
                    "id": 9919,
                    "node_id": "MDEyOk9yZ2FuaXphdGlvbjk5MTk=",
                    "avatar_url": "https://avatars.githubusercontent.com/u/9919?v=4",
                    "gravatar_id": "",
                    "url": "https://api.github.com/users/github",
                    "html_url": "https://github.com/github",
                    "followers_url": "https://api.github.com/users/github/followers",
                    "following_url": "https://api.github.com/users/github/following{/other_user}",
                    "gists_url": "https://api.github.com/users/github/gists{/gist_id}",
                    "starred_url": "https://api.github.com/users/github/starred{/owner}{/repo}",
                    "subscriptions_url": "https://api.github.com/users/github/subscriptions",
                    "organizations_url": "https://api.github.com/users/github/orgs",
                    "repos_url": "https://api.github.com/users/github/repos",
                    "events_url": "https://api.github.com/users/github/events{/privacy}",
                    "received_events_url": "https://api.github.com/users/github/received_events",
                    "type": "Organization",
                    "site_admin": false
                },
                "created_at": "2022-07-04T22:19:11Z",
                "updated_at": "2022-07-04T22:20:11Z"
            },
            {
                "id": 8031,
                "name": "Auditor",
                "description": "Permissions to read the organization audit log",
                "permissions": [
                    "read_audit_logs"
                ],
                "organization": {
                    "login": "github",
                    "id": 9919,
                    "node_id": "MDEyOk9yZ2FuaXphdGlvbjk5MTk=",
                    "avatar_url": "https://avatars.githubusercontent.com/u/9919?v=4",
                    "gravatar_id": "",
                    "url": "https://api.github.com/users/github",
                    "html_url": "https://github.com/github",
                    "followers_url": "https://api.github.com/users/github/followers",
                    "following_url": "https://api.github.com/users/github/following{/other_user}",
                    "gists_url": "https://api.github.com/users/github/gists{/gist_id}",
                    "starred_url": "https://api.github.com/users/github/starred{/owner}{/repo}",
                    "subscriptions_url": "https://api.github.com/users/github/subscriptions",
                    "organizations_url": "https://api.github.com/users/github/orgs",
                    "repos_url": "https://api.github.com/users/github/repos",
                    "events_url": "https://api.github.com/users/github/events{/privacy}",
                    "received_events_url": "https://api.github.com/users/github/received_events",
                    "type": "Organization",
                    "site_admin": false
                },
                "created_at": "2022-07-04T22:19:11Z",
                "updated_at": "2022-07-04T22:20:11Z"
            }
        ]
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