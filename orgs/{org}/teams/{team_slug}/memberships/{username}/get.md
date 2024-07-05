# Get team membership for a user

`get /orgs/{org}/teams/{team_slug}/memberships/{username}`

Team members will include the members of child teams.

To get a user's membership with a team, the team must be visible to the authenticated user.

**Note:** You can also specify a team by `org_id` and `team_id` using the route `GET /organizations/{org_id}/team/{team_id}/memberships/{username}`.

**Note:**
The response contains the `state` of the membership and the member's `role`.

The `role` for organization owners is set to `maintainer`. For more information about `maintainer` roles, see [Create a team](https://docs.github.com/rest/teams/teams#create-a-team).

## Operation Object

```json
{
    "summary": "Get team membership for a user",
    "description": "Team members will include the members of child teams.\n\nTo get a user's membership with a team, the team must be visible to the authenticated user.\n\n**Note:** You can also specify a team by `org_id` and `team_id` using the route `GET /organizations/{org_id}/team/{team_id}/memberships/{username}`.\n\n**Note:**\nThe response contains the `state` of the membership and the member's `role`.\n\nThe `role` for organization owners is set to `maintainer`. For more information about `maintainer` roles, see [Create a team](https://docs.github.com/rest/teams/teams#create-a-team).",
    "tags": [
        "teams"
    ],
    "operationId": "teams/get-membership-for-user-in-org",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/teams/members#get-team-membership-for-a-user"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/org"
        },
        {
            "$ref": "#/components/parameters/team-slug"
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
            "description": "if user has no team membership"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "teams",
        "subcategory": "members"
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