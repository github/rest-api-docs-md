# Check team permissions for a project (Legacy)

**Deprecation Notice:** This endpoint route is deprecated and will be removed from the Teams API. We recommend migrating your existing code to use the new [Check team permissions for a project](https://docs.github.com/rest/teams/teams#check-team-permissions-for-a-project) endpoint.

Checks whether a team has `read`, `write`, or `admin` permissions for an organization project. The response includes projects inherited from a parent team.

## Operation Object

```json
{
    "summary": "Check team permissions for a project (Legacy)",
    "description": "**Deprecation Notice:** This endpoint route is deprecated and will be removed from the Teams API. We recommend migrating your existing code to use the new [Check team permissions for a project](https://docs.github.com/rest/teams/teams#check-team-permissions-for-a-project) endpoint.\n\nChecks whether a team has `read`, `write`, or `admin` permissions for an organization project. The response includes projects inherited from a parent team.",
    "tags": [
        "teams"
    ],
    "operationId": "teams/check-permissions-for-project-legacy",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/teams/teams#check-team-permissions-for-a-project-legacy"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/team-id"
        },
        {
            "$ref": "#/components/parameters/project-id"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/team-project"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/team-project"
                        }
                    }
                }
            }
        },
        "404": {
            "description": "Not Found if project is not managed by this team"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "removalDate": "2021-02-01",
        "deprecationDate": "2020-01-21",
        "category": "teams",
        "subcategory": "teams"
    },
    "deprecated": true
}
```

## References

### `#/components/parameters/team-id`

```json
{
    "name": "team_id",
    "description": "The unique identifier of the team.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "integer"
    }
}
```

### `#/components/parameters/project-id`

```json
{
    "name": "project_id",
    "description": "The unique identifier of the project.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "integer"
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

### `#/components/examples/team-project`

```json
{
    "value": {
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
}
```