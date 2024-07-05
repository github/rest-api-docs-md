# Get team membership for a user (Legacy)

**Deprecation Notice:** This endpoint route is deprecated and will be removed from the Teams API. We recommend migrating your existing code to use the new [Get team membership for a user](https://docs.github.com/rest/teams/members#get-team-membership-for-a-user) endpoint.

Team members will include the members of child teams.

To get a user's membership with a team, the team must be visible to the authenticated user.

**Note:**
The response contains the `state` of the membership and the member's `role`.

The `role` for organization owners is set to `maintainer`. For more information about `maintainer` roles, see [Create a team](https://docs.github.com/rest/teams/teams#create-a-team).

## Operation Object

```json
{
    "summary": "Get team membership for a user (Legacy)",
    "description": "**Deprecation Notice:** This endpoint route is deprecated and will be removed from the Teams API. We recommend migrating your existing code to use the new [Get team membership for a user](https://docs.github.com/rest/teams/members#get-team-membership-for-a-user) endpoint.\n\nTeam members will include the members of child teams.\n\nTo get a user's membership with a team, the team must be visible to the authenticated user.\n\n**Note:**\nThe response contains the `state` of the membership and the member's `role`.\n\nThe `role` for organization owners is set to `maintainer`. For more information about `maintainer` roles, see [Create a team](https://docs.github.com/rest/teams/teams#create-a-team).",
    "tags": [
        "teams"
    ],
    "operationId": "teams/get-membership-for-user-legacy",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/teams/members#get-team-membership-for-a-user-legacy"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/team-id"
        },
        {
            "$ref": "#/components/parameters/username"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/team-membership"
                    },
                    "examples": {
                        "response-if-user-is-a-team-maintainer": {
                            "$ref": "#/components/examples/team-membership-response-if-user-is-a-team-maintainer"
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
        "removalDate": "2021-02-01",
        "deprecationDate": "2020-01-21",
        "category": "teams",
        "subcategory": "members"
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

### `#/components/parameters/username`

```json
{
    "name": "username",
    "description": "The handle for the GitHub user account.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "string"
    }
}
```

### `#/components/schemas/team-membership`

```json
{
    "title": "Team Membership",
    "description": "Team Membership",
    "type": "object",
    "properties": {
        "url": {
            "type": "string",
            "format": "uri"
        },
        "role": {
            "description": "The role of the user in the team.",
            "enum": [
                "member",
                "maintainer"
            ],
            "default": "member",
            "example": "member",
            "type": "string"
        },
        "state": {
            "description": "The state of the user's membership in the team.",
            "type": "string",
            "enum": [
                "active",
                "pending"
            ]
        }
    },
    "required": [
        "role",
        "state",
        "url"
    ]
}
```

### `#/components/examples/team-membership-response-if-user-is-a-team-maintainer`

```json
{
    "summary": "Response if user is a team maintainer",
    "value": {
        "url": "https://api.github.com/teams/1/memberships/octocat",
        "role": "maintainer",
        "state": "active"
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