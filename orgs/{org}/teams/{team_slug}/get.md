# Get a team by name

Gets a team using the team's `slug`. To create the `slug`, GitHub replaces special characters in the `name` string, changes all words to lowercase, and replaces spaces with a `-` separator. For example, `"My TEam Näme"` would become `my-team-name`.

**Note:** You can also specify a team by `org_id` and `team_id` using the route `GET /organizations/{org_id}/team/{team_id}`.

## Operation Object

```json
{
    "summary": "Get a team by name",
    "description": "Gets a team using the team's `slug`. To create the `slug`, GitHub replaces special characters in the `name` string, changes all words to lowercase, and replaces spaces with a `-` separator. For example, `\"My TEam N\u00e4me\"` would become `my-team-name`.\n\n**Note:** You can also specify a team by `org_id` and `team_id` using the route `GET /organizations/{org_id}/team/{team_id}`.",
    "tags": [
        "teams"
    ],
    "operationId": "teams/get-by-name",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/teams/teams#get-a-team-by-name"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/org"
        },
        {
            "$ref": "#/components/parameters/team-slug"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/team-full"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/team-full"
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
        "category": "teams",
        "subcategory": "teams"
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

### `#/components/parameters/team-slug`

```json
{
    "name": "team_slug",
    "description": "The slug of the team name.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "string"
    }
}
```

### `#/components/schemas/team-full`

```json
{
    "title": "Full Team",
    "description": "Groups of organization members that gives permissions on specified repositories.",
    "type": "object",
    "properties": {
        "id": {
            "description": "Unique identifier of the team",
            "example": 42,
            "type": "integer"
        },
        "node_id": {
            "type": "string",
            "example": "MDQ6VGVhbTE="
        },
        "url": {
            "description": "URL for the team",
            "example": "https://api.github.com/organizations/1/team/1",
            "type": "string",
            "format": "uri"
        },
        "html_url": {
            "type": "string",
            "format": "uri",
            "example": "https://github.com/orgs/rails/teams/core"
        },
        "name": {
            "description": "Name of the team",
            "example": "Developers",
            "type": "string"
        },
        "slug": {
            "type": "string",
            "example": "justice-league"
        },
        "description": {
            "type": "string",
            "example": "A great team.",
            "nullable": true
        },
        "privacy": {
            "description": "The level of privacy this team should have",
            "type": "string",
            "enum": [
                "closed",
                "secret"
            ],
            "example": "closed"
        },
        "notification_setting": {
            "description": "The notification setting the team has set",
            "type": "string",
            "enum": [
                "notifications_enabled",
                "notifications_disabled"
            ],
            "example": "notifications_enabled"
        },
        "permission": {
            "description": "Permission that the team will have for its repositories",
            "example": "push",
            "type": "string"
        },
        "members_url": {
            "type": "string",
            "example": "https://api.github.com/organizations/1/team/1/members{/member}"
        },
        "repositories_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/organizations/1/team/1/repos"
        },
        "parent": {
            "$ref": "#/components/schemas/nullable-team-simple"
        },
        "members_count": {
            "type": "integer",
            "example": 3
        },
        "repos_count": {
            "type": "integer",
            "example": 10
        },
        "created_at": {
            "type": "string",
            "format": "date-time",
            "example": "2017-07-14T16:53:42Z"
        },
        "updated_at": {
            "type": "string",
            "format": "date-time",
            "example": "2017-08-17T12:37:15Z"
        },
        "organization": {
            "$ref": "#/components/schemas/team-organization"
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
        "slug",
        "created_at",
        "updated_at",
        "members_count",
        "repos_count",
        "organization"
    ]
}
```

### `#/components/examples/team-full`

```json
{
    "value": {
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
        "parent": null,
        "members_count": 3,
        "repos_count": 10,
        "created_at": "2017-07-14T16:53:42Z",
        "updated_at": "2017-08-17T12:37:15Z",
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
            "description": "A great organization",
            "name": "github",
            "company": "GitHub",
            "blog": "https://github.com/blog",
            "location": "San Francisco",
            "email": "octocat@github.com",
            "is_verified": true,
            "has_organization_projects": true,
            "has_repository_projects": true,
            "public_repos": 2,
            "public_gists": 1,
            "followers": 20,
            "following": 0,
            "html_url": "https://github.com/octocat",
            "created_at": "2008-01-14T04:33:35Z",
            "updated_at": "2017-08-17T12:37:15Z",
            "type": "Organization"
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