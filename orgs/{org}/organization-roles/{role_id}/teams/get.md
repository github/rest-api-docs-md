# List teams that are assigned to an organization role

Lists the teams that are assigned to an organization role. For more information on organization roles, see "[Managing people's access to your organization with roles](https://docs.github.com/organizations/managing-peoples-access-to-your-organization-with-roles/about-custom-organization-roles)."

To use this endpoint, you must be an administrator for the organization.

OAuth app tokens and personal access tokens (classic) need the `admin:org` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "List teams that are assigned to an organization role",
    "description": "Lists the teams that are assigned to an organization role. For more information on organization roles, see \"[Managing people's access to your organization with roles](https://docs.github.com/organizations/managing-peoples-access-to-your-organization-with-roles/about-custom-organization-roles).\"\n\nTo use this endpoint, you must be an administrator for the organization.\n\nOAuth app tokens and personal access tokens (classic) need the `admin:org` scope to use this endpoint.",
    "tags": [
        "orgs"
    ],
    "operationId": "orgs/list-org-role-teams",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/orgs/organization-roles#list-teams-that-are-assigned-to-an-organization-role"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/org"
        },
        {
            "$ref": "#/components/parameters/role-id"
        },
        {
            "$ref": "#/components/parameters/per-page"
        },
        {
            "$ref": "#/components/parameters/page"
        }
    ],
    "responses": {
        "200": {
            "description": "Response - List of assigned teams",
            "content": {
                "application/json": {
                    "schema": {
                        "type": "array",
                        "description": "List of teams assigned to the organization role",
                        "items": {
                            "$ref": "#/components/schemas/team-role-assignment"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/team-items"
                        }
                    }
                }
            },
            "headers": {
                "Link": {
                    "$ref": "#/components/headers/link"
                }
            }
        },
        "404": {
            "description": "Response if the organization or role does not exist."
        },
        "422": {
            "description": "Response if the organization roles feature is not enabled or validation failed."
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

### `#/components/parameters/per-page`

```json
{
    "name": "per_page",
    "description": "The number of results per page (max 100). For more information, see \"[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api).\"",
    "in": "query",
    "schema": {
        "type": "integer",
        "default": 30
    }
}
```

### `#/components/parameters/page`

```json
{
    "name": "page",
    "description": "The page number of the results to fetch. For more information, see \"[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api).\"",
    "in": "query",
    "schema": {
        "type": "integer",
        "default": 1
    }
}
```

### `#/components/schemas/team-role-assignment`

```json
{
    "title": "A Role Assignment for a Team",
    "description": "The Relationship a Team has with a role.",
    "type": "object",
    "properties": {
        "id": {
            "type": "integer"
        },
        "node_id": {
            "type": "string"
        },
        "name": {
            "type": "string"
        },
        "slug": {
            "type": "string"
        },
        "description": {
            "type": "string",
            "nullable": true
        },
        "privacy": {
            "type": "string"
        },
        "notification_setting": {
            "type": "string"
        },
        "permission": {
            "type": "string"
        },
        "permissions": {
            "type": "object",
            "properties": {
                "pull": {
                    "type": "boolean"
                },
                "triage": {
                    "type": "boolean"
                },
                "push": {
                    "type": "boolean"
                },
                "maintain": {
                    "type": "boolean"
                },
                "admin": {
                    "type": "boolean"
                }
            },
            "required": [
                "pull",
                "triage",
                "push",
                "maintain",
                "admin"
            ]
        },
        "url": {
            "type": "string",
            "format": "uri"
        },
        "html_url": {
            "type": "string",
            "format": "uri",
            "example": "https://github.com/orgs/rails/teams/core"
        },
        "members_url": {
            "type": "string"
        },
        "repositories_url": {
            "type": "string",
            "format": "uri"
        },
        "parent": {
            "$ref": "#/components/schemas/nullable-team-simple"
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
        "slug",
        "parent"
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

### `#/components/headers/link`

```json
{
    "example": "<https://api.github.com/resource?page=2>; rel=\"next\", <https://api.github.com/resource?page=5>; rel=\"last\"",
    "schema": {
        "type": "string"
    }
}
```