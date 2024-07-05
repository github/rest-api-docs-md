# List security manager teams

`get /orgs/{org}/security-managers`

Lists teams that are security managers for an organization. For more information, see "[Managing security managers in your organization](https://docs.github.com/organizations/managing-peoples-access-to-your-organization-with-roles/managing-security-managers-in-your-organization)."

The authenticated user must be an administrator or security manager for the organization to use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `read:org` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "List security manager teams",
    "description": "Lists teams that are security managers for an organization. For more information, see \"[Managing security managers in your organization](https://docs.github.com/organizations/managing-peoples-access-to-your-organization-with-roles/managing-security-managers-in-your-organization).\"\n\nThe authenticated user must be an administrator or security manager for the organization to use this endpoint.\n\nOAuth app tokens and personal access tokens (classic) need the `read:org` scope to use this endpoint.",
    "tags": [
        "orgs"
    ],
    "operationId": "orgs/list-security-manager-teams",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/orgs/security-managers#list-security-manager-teams"
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
                            "$ref": "#/components/schemas/team-simple"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/team-items"
                        }
                    }
                }
            }
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "previews": [],
        "category": "orgs",
        "subcategory": "security-managers"
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

### `#/components/schemas/team-simple`

```json
{
    "title": "Team Simple",
    "description": "Groups of organization members that gives permissions on specified repositories.",
    "type": "object",
    "properties": {
        "id": {
            "description": "Unique identifier of the team",
            "type": "integer",
            "example": 1
        },
        "node_id": {
            "type": "string",
            "example": "MDQ6VGVhbTE="
        },
        "url": {
            "description": "URL for the team",
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/organizations/1/team/1"
        },
        "members_url": {
            "type": "string",
            "example": "https://api.github.com/organizations/1/team/1/members{/member}"
        },
        "name": {
            "description": "Name of the team",
            "type": "string",
            "example": "Justice League"
        },
        "description": {
            "description": "Description of the team",
            "type": "string",
            "nullable": true,
            "example": "A great team."
        },
        "permission": {
            "description": "Permission that the team will have for its repositories",
            "type": "string",
            "example": "admin"
        },
        "privacy": {
            "description": "The level of privacy this team should have",
            "type": "string",
            "example": "closed"
        },
        "notification_setting": {
            "description": "The notification setting the team has set",
            "type": "string",
            "example": "notifications_enabled"
        },
        "html_url": {
            "type": "string",
            "format": "uri",
            "example": "https://github.com/orgs/rails/teams/core"
        },
        "repositories_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/organizations/1/team/1/repos"
        },
        "slug": {
            "type": "string",
            "example": "justice-league"
        },
        "ldap_dn": {
            "description": "Distinguished Name (DN) that team maps to within LDAP environment",
            "example": "uid=example,ou=users,dc=github,dc=com",
            "type": "string"
        }
    },
    "required": [
        "id",
        "node_id",
        "url",
        "members_url",
        "name",
        "description",
        "permission",
        "html_url",
        "repositories_url",
        "slug"
    ]
}
```

### `#/components/examples/team-items`

```json
{
    "value": [
        {
            "id": 1,
            "node_id": "MDQ6VGVhbTE=",
            "url": "https://api.github.com/teams/1",
            "html_url": "https://github.com/orgs/github/teams/justice-league",
            "name": "Justice League",
            "slug": "justice-league",
            "description": "A great team.",
            "privacy": "closed",
            "notification_setting": "notifications_enabled",
            "permission": "admin",
            "members_url": "https://api.github.com/teams/1/members{/member}",
            "repositories_url": "https://api.github.com/teams/1/repos",
            "parent": null
        }
    ]
}
```