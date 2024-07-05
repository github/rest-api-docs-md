# List team projects

Lists the organization projects for a team.

**Note:** You can also specify a team by `org_id` and `team_id` using the route `GET /organizations/{org_id}/team/{team_id}/projects`.

## Operation Object

```json
{
    "summary": "List team projects",
    "description": "Lists the organization projects for a team.\n\n**Note:** You can also specify a team by `org_id` and `team_id` using the route `GET /organizations/{org_id}/team/{team_id}/projects`.",
    "tags": [
        "teams"
    ],
    "operationId": "teams/list-projects-in-org",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/teams/teams#list-team-projects"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/org"
        },
        {
            "$ref": "#/components/parameters/team-slug"
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
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "type": "array",
                        "items": {
                            "$ref": "#/components/schemas/team-project"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/team-project-items"
                        }
                    }
                }
            },
            "headers": {
                "Link": {
                    "$ref": "#/components/headers/link"
                }
            }
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

### `#/components/schemas/team-project`

```json
{
    "title": "Team Project",
    "description": "A team's access to a project.",
    "type": "object",
    "properties": {
        "owner_url": {
            "type": "string"
        },
        "url": {
            "type": "string"
        },
        "html_url": {
            "type": "string"
        },
        "columns_url": {
            "type": "string"
        },
        "id": {
            "type": "integer"
        },
        "node_id": {
            "type": "string"
        },
        "name": {
            "type": "string"
        },
        "body": {
            "type": "string",
            "nullable": true
        },
        "number": {
            "type": "integer"
        },
        "state": {
            "type": "string"
        },
        "creator": {
            "$ref": "#/components/schemas/simple-user"
        },
        "created_at": {
            "type": "string"
        },
        "updated_at": {
            "type": "string"
        },
        "organization_permission": {
            "description": "The organization permission for this project. Only present when owner is an organization.",
            "type": "string"
        },
        "private": {
            "description": "Whether the project is private or not. Only present when owner is an organization.",
            "type": "boolean"
        },
        "permissions": {
            "type": "object",
            "properties": {
                "read": {
                    "type": "boolean"
                },
                "write": {
                    "type": "boolean"
                },
                "admin": {
                    "type": "boolean"
                }
            },
            "required": [
                "read",
                "write",
                "admin"
            ]
        }
    },
    "required": [
        "owner_url",
        "url",
        "html_url",
        "columns_url",
        "id",
        "node_id",
        "name",
        "body",
        "number",
        "state",
        "creator",
        "created_at",
        "updated_at",
        "permissions"
    ]
}
```

### `#/components/examples/team-project-items`

```json
{
    "value": [
        {
            "owner_url": "https://api.github.com/orgs/octocat",
            "url": "https://api.github.com/projects/1002605",
            "html_url": "https://github.com/orgs/api-playground/projects/1",
            "columns_url": "https://api.github.com/projects/1002605/columns",
            "id": 1002605,
            "node_id": "MDc6UHJvamVjdDEwMDI2MDU=",
            "name": "Organization Roadmap",
            "body": "High-level roadmap for the upcoming year.",
            "number": 1,
            "state": "open",
            "creator": {
                "login": "octocat",
                "id": 1,
                "node_id": "MDQ6VXNlcjE=",
                "avatar_url": "https://github.com/images/error/octocat_happy.gif",
                "gravatar_id": "",
                "url": "https://api.github.com/users/octocat",
                "html_url": "https://github.com/octocat",
                "followers_url": "https://api.github.com/users/octocat/followers",
                "following_url": "https://api.github.com/users/octocat/following{/other_user}",
                "gists_url": "https://api.github.com/users/octocat/gists{/gist_id}",
                "starred_url": "https://api.github.com/users/octocat/starred{/owner}{/repo}",
                "subscriptions_url": "https://api.github.com/users/octocat/subscriptions",
                "organizations_url": "https://api.github.com/users/octocat/orgs",
                "repos_url": "https://api.github.com/users/octocat/repos",
                "events_url": "https://api.github.com/users/octocat/events{/privacy}",
                "received_events_url": "https://api.github.com/users/octocat/received_events",
                "type": "User",
                "site_admin": false
            },
            "created_at": "2011-04-11T20:09:31Z",
            "updated_at": "2014-03-04T18:58:10Z",
            "organization_permission": "write",
            "private": false,
            "permissions": {
                "read": true,
                "write": true,
                "admin": false
            }
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