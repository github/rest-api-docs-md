# Get an organization

`get /orgs/{org}`

Gets information about an organization.

When the value of `two_factor_requirement_enabled` is `true`, the organization requires all members, billing managers, and outside collaborators to enable [two-factor authentication](https://docs.github.com/articles/securing-your-account-with-two-factor-authentication-2fa/).

To see the full details about an organization, the authenticated user must be an organization owner.

The values returned by this endpoint are set by the "Update an organization" endpoint. If your organization set a default security configuration (beta), the following values retrieved from the "Update an organization" endpoint have been overwritten by that configuration:

- advanced_security_enabled_for_new_repositories
- dependabot_alerts_enabled_for_new_repositories
- dependabot_security_updates_enabled_for_new_repositories
- dependency_graph_enabled_for_new_repositories
- secret_scanning_enabled_for_new_repositories
- secret_scanning_push_protection_enabled_for_new_repositories

For more information on security configurations, see "[Enabling security features at scale](https://docs.github.com/code-security/securing-your-organization/introduction-to-securing-your-organization-at-scale/about-enabling-security-features-at-scale)."

OAuth app tokens and personal access tokens (classic) need the `admin:org` scope to see the full details about an organization.

To see information about an organization's GitHub plan, GitHub Apps need the `Organization plan` permission.

## Operation Object

```json
{
    "summary": "Get an organization",
    "description": "Gets information about an organization.\n\nWhen the value of `two_factor_requirement_enabled` is `true`, the organization requires all members, billing managers, and outside collaborators to enable [two-factor authentication](https://docs.github.com/articles/securing-your-account-with-two-factor-authentication-2fa/).\n\nTo see the full details about an organization, the authenticated user must be an organization owner.\n\nThe values returned by this endpoint are set by the \"Update an organization\" endpoint. If your organization set a default security configuration (beta), the following values retrieved from the \"Update an organization\" endpoint have been overwritten by that configuration:\n\n- advanced_security_enabled_for_new_repositories\n- dependabot_alerts_enabled_for_new_repositories\n- dependabot_security_updates_enabled_for_new_repositories\n- dependency_graph_enabled_for_new_repositories\n- secret_scanning_enabled_for_new_repositories\n- secret_scanning_push_protection_enabled_for_new_repositories\n\nFor more information on security configurations, see \"[Enabling security features at scale](https://docs.github.com/code-security/securing-your-organization/introduction-to-securing-your-organization-at-scale/about-enabling-security-features-at-scale).\"\n\nOAuth app tokens and personal access tokens (classic) need the `admin:org` scope to see the full details about an organization.\n\nTo see information about an organization's GitHub plan, GitHub Apps need the `Organization plan` permission.",
    "tags": [
        "orgs"
    ],
    "operationId": "orgs/get",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/orgs/orgs#get-an-organization"
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
                        "$ref": "#/components/schemas/organization-full"
                    },
                    "examples": {
                        "default-response": {
                            "$ref": "#/components/examples/organization-full"
                        }
                    }
                }
            }
        },
        "404": {
            "$ref": "#/components/responses/not_found"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "orgs",
        "subcategory": "orgs"
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

### `#/components/schemas/organization-full`

```json
{
    "title": "Organization Full",
    "description": "Organization Full",
    "type": "object",
    "properties": {
        "login": {
            "type": "string",
            "example": "github"
        },
        "id": {
            "type": "integer",
            "example": 1
        },
        "node_id": {
            "type": "string",
            "example": "MDEyOk9yZ2FuaXphdGlvbjE="
        },
        "url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/orgs/github"
        },
        "repos_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/orgs/github/repos"
        },
        "events_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/orgs/github/events"
        },
        "hooks_url": {
            "type": "string",
            "example": "https://api.github.com/orgs/github/hooks"
        },
        "issues_url": {
            "type": "string",
            "example": "https://api.github.com/orgs/github/issues"
        },
        "members_url": {
            "type": "string",
            "example": "https://api.github.com/orgs/github/members{/member}"
        },
        "public_members_url": {
            "type": "string",
            "example": "https://api.github.com/orgs/github/public_members{/member}"
        },
        "avatar_url": {
            "type": "string",
            "example": "https://github.com/images/error/octocat_happy.gif"
        },
        "description": {
            "type": "string",
            "example": "A great organization",
            "nullable": true
        },
        "name": {
            "type": "string",
            "example": "github"
        },
        "company": {
            "type": "string",
            "example": "GitHub"
        },
        "blog": {
            "type": "string",
            "format": "uri",
            "example": "https://github.com/blog"
        },
        "location": {
            "type": "string",
            "example": "San Francisco"
        },
        "email": {
            "type": "string",
            "format": "email",
            "example": "octocat@github.com"
        },
        "twitter_username": {
            "type": "string",
            "example": "github",
            "nullable": true
        },
        "is_verified": {
            "type": "boolean",
            "example": true
        },
        "has_organization_projects": {
            "type": "boolean",
            "example": true
        },
        "has_repository_projects": {
            "type": "boolean",
            "example": true
        },
        "public_repos": {
            "type": "integer",
            "example": 2
        },
        "public_gists": {
            "type": "integer",
            "example": 1
        },
        "followers": {
            "type": "integer",
            "example": 20
        },
        "following": {
            "type": "integer",
            "example": 0
        },
        "html_url": {
            "type": "string",
            "format": "uri",
            "example": "https://github.com/octocat"
        },
        "type": {
            "type": "string",
            "example": "Organization"
        },
        "total_private_repos": {
            "type": "integer",
            "example": 100
        },
        "owned_private_repos": {
            "type": "integer",
            "example": 100
        },
        "private_gists": {
            "type": "integer",
            "example": 81,
            "nullable": true
        },
        "disk_usage": {
            "type": "integer",
            "example": 10000,
            "nullable": true
        },
        "collaborators": {
            "type": "integer",
            "example": 8,
            "nullable": true
        },
        "billing_email": {
            "type": "string",
            "format": "email",
            "example": "org@example.com",
            "nullable": true
        },
        "plan": {
            "type": "object",
            "properties": {
                "name": {
                    "type": "string"
                },
                "space": {
                    "type": "integer"
                },
                "private_repos": {
                    "type": "integer"
                },
                "filled_seats": {
                    "type": "integer"
                },
                "seats": {
                    "type": "integer"
                }
            },
            "required": [
                "name",
                "space",
                "private_repos"
            ]
        },
        "default_repository_permission": {
            "type": "string",
            "nullable": true
        },
        "members_can_create_repositories": {
            "type": "boolean",
            "example": true,
            "nullable": true
        },
        "two_factor_requirement_enabled": {
            "type": "boolean",
            "example": true,
            "nullable": true
        },
        "members_allowed_repository_creation_type": {
            "type": "string",
            "example": "all"
        },
        "members_can_create_public_repositories": {
            "type": "boolean",
            "example": true
        },
        "members_can_create_private_repositories": {
            "type": "boolean",
            "example": true
        },
        "members_can_create_internal_repositories": {
            "type": "boolean",
            "example": true
        },
        "members_can_create_pages": {
            "type": "boolean",
            "example": true
        },
        "members_can_create_public_pages": {
            "type": "boolean",
            "example": true
        },
        "members_can_create_private_pages": {
            "type": "boolean",
            "example": true
        },
        "members_can_fork_private_repositories": {
            "type": "boolean",
            "example": false,
            "nullable": true
        },
        "web_commit_signoff_required": {
            "type": "boolean",
            "example": false
        },
        "advanced_security_enabled_for_new_repositories": {
            "type": "boolean",
            "example": false,
            "description": "Whether GitHub Advanced Security is enabled for new repositories and repositories transferred to this organization.\n\nThis field is only visible to organization owners or members of a team with the security manager role."
        },
        "dependabot_alerts_enabled_for_new_repositories": {
            "type": "boolean",
            "example": false,
            "description": "Whether GitHub Advanced Security is automatically enabled for new repositories and repositories transferred to\nthis organization.\n\nThis field is only visible to organization owners or members of a team with the security manager role."
        },
        "dependabot_security_updates_enabled_for_new_repositories": {
            "type": "boolean",
            "example": false,
            "description": "Whether dependabot security updates are automatically enabled for new repositories and repositories transferred\nto this organization.\n\nThis field is only visible to organization owners or members of a team with the security manager role."
        },
        "dependency_graph_enabled_for_new_repositories": {
            "type": "boolean",
            "example": false,
            "description": "Whether dependency graph is automatically enabled for new repositories and repositories transferred to this\norganization.\n\nThis field is only visible to organization owners or members of a team with the security manager role."
        },
        "secret_scanning_enabled_for_new_repositories": {
            "type": "boolean",
            "example": false,
            "description": "Whether secret scanning is automatically enabled for new repositories and repositories transferred to this\norganization.\n\nThis field is only visible to organization owners or members of a team with the security manager role."
        },
        "secret_scanning_push_protection_enabled_for_new_repositories": {
            "type": "boolean",
            "example": false,
            "description": "Whether secret scanning push protection is automatically enabled for new repositories and repositories\ntransferred to this organization.\n\nThis field is only visible to organization owners or members of a team with the security manager role."
        },
        "secret_scanning_push_protection_custom_link_enabled": {
            "type": "boolean",
            "example": false,
            "description": "Whether a custom link is shown to contributors who are blocked from pushing a secret by push protection."
        },
        "secret_scanning_push_protection_custom_link": {
            "type": "string",
            "example": "https://github.com/test-org/test-repo/blob/main/README.md",
            "nullable": true,
            "description": "An optional URL string to display to contributors who are blocked from pushing a secret."
        },
        "created_at": {
            "type": "string",
            "format": "date-time",
            "example": "2008-01-14T04:33:35Z"
        },
        "updated_at": {
            "type": "string",
            "format": "date-time"
        },
        "archived_at": {
            "type": "string",
            "format": "date-time",
            "nullable": true
        }
    },
    "required": [
        "login",
        "url",
        "id",
        "node_id",
        "repos_url",
        "events_url",
        "hooks_url",
        "issues_url",
        "members_url",
        "public_members_url",
        "avatar_url",
        "description",
        "html_url",
        "has_organization_projects",
        "has_repository_projects",
        "public_repos",
        "public_gists",
        "followers",
        "following",
        "type",
        "created_at",
        "updated_at",
        "archived_at"
    ]
}
```

### `#/components/examples/organization-full`

```json
{
    "value": {
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
        "description": "A great organization",
        "name": "github",
        "company": "GitHub",
        "blog": "https://github.com/blog",
        "location": "San Francisco",
        "email": "octocat@github.com",
        "twitter_username": "github",
        "is_verified": true,
        "has_organization_projects": true,
        "has_repository_projects": true,
        "public_repos": 2,
        "public_gists": 1,
        "followers": 20,
        "following": 0,
        "html_url": "https://github.com/octocat",
        "created_at": "2008-01-14T04:33:35Z",
        "type": "Organization",
        "total_private_repos": 100,
        "owned_private_repos": 100,
        "private_gists": 81,
        "disk_usage": 10000,
        "collaborators": 8,
        "billing_email": "mona@github.com",
        "plan": {
            "name": "Medium",
            "space": 400,
            "private_repos": 20,
            "filled_seats": 4,
            "seats": 5
        },
        "default_repository_permission": "read",
        "members_can_create_repositories": true,
        "two_factor_requirement_enabled": true,
        "members_allowed_repository_creation_type": "all",
        "members_can_create_public_repositories": false,
        "members_can_create_private_repositories": false,
        "members_can_create_internal_repositories": false,
        "members_can_create_pages": true,
        "members_can_create_public_pages": true,
        "members_can_create_private_pages": true,
        "members_can_fork_private_repositories": false,
        "web_commit_signoff_required": false,
        "updated_at": "2014-03-03T18:58:10Z",
        "dependency_graph_enabled_for_new_repositories": false,
        "dependabot_alerts_enabled_for_new_repositories": false,
        "dependabot_security_updates_enabled_for_new_repositories": false,
        "advanced_security_enabled_for_new_repositories": false,
        "secret_scanning_enabled_for_new_repositories": false,
        "secret_scanning_push_protection_enabled_for_new_repositories": false,
        "secret_scanning_push_protection_custom_link": "https://github.com/octo-org/octo-repo/blob/main/im-blocked.md",
        "secret_scanning_push_protection_custom_link_enabled": false
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