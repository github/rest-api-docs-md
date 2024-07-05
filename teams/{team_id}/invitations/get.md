# List pending team invitations (Legacy)

**Deprecation Notice:** This endpoint route is deprecated and will be removed from the Teams API. We recommend migrating your existing code to use the new [`List pending team invitations`](https://docs.github.com/rest/teams/members#list-pending-team-invitations) endpoint.

The return hash contains a `role` field which refers to the Organization Invitation role and will be one of the following values: `direct_member`, `admin`, `billing_manager`, `hiring_manager`, or `reinstate`. If the invitee is not a GitHub member, the `login` field in the return hash will be `null`.

## Operation Object

```json
{
    "summary": "List pending team invitations (Legacy)",
    "description": "**Deprecation Notice:** This endpoint route is deprecated and will be removed from the Teams API. We recommend migrating your existing code to use the new [`List pending team invitations`](https://docs.github.com/rest/teams/members#list-pending-team-invitations) endpoint.\n\nThe return hash contains a `role` field which refers to the Organization Invitation role and will be one of the following values: `direct_member`, `admin`, `billing_manager`, `hiring_manager`, or `reinstate`. If the invitee is not a GitHub member, the `login` field in the return hash will be `null`.",
    "tags": [
        "teams"
    ],
    "operationId": "teams/list-pending-invitations-legacy",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/teams/members#list-pending-team-invitations-legacy"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/team-id"
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
                            "$ref": "#/components/schemas/organization-invitation"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/organization-invitation-items"
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

### `#/components/schemas/organization-invitation`

```json
{
    "title": "Organization Invitation",
    "description": "Organization Invitation",
    "type": "object",
    "properties": {
        "id": {
            "type": "integer",
            "format": "int64"
        },
        "login": {
            "type": "string",
            "nullable": true
        },
        "email": {
            "type": "string",
            "nullable": true
        },
        "role": {
            "type": "string"
        },
        "created_at": {
            "type": "string"
        },
        "failed_at": {
            "type": "string",
            "nullable": true
        },
        "failed_reason": {
            "type": "string",
            "nullable": true
        },
        "inviter": {
            "$ref": "#/components/schemas/simple-user"
        },
        "team_count": {
            "type": "integer"
        },
        "node_id": {
            "type": "string",
            "example": "\"MDIyOk9yZ2FuaXphdGlvbkludml0YXRpb24x\""
        },
        "invitation_teams_url": {
            "type": "string",
            "example": "\"https://api.github.com/organizations/16/invitations/1/teams\""
        },
        "invitation_source": {
            "type": "string",
            "example": "\"member\""
        }
    },
    "required": [
        "id",
        "login",
        "email",
        "role",
        "created_at",
        "inviter",
        "team_count",
        "invitation_teams_url",
        "node_id"
    ]
}
```

### `#/components/examples/organization-invitation-items`

```json
{
    "value": [
        {
            "id": 1,
            "login": "monalisa",
            "node_id": "MDQ6VXNlcjE=",
            "email": "octocat@github.com",
            "role": "direct_member",
            "created_at": "2016-11-30T06:46:10-08:00",
            "failed_at": "",
            "failed_reason": "",
            "inviter": {
                "login": "other_user",
                "id": 1,
                "node_id": "MDQ6VXNlcjE=",
                "avatar_url": "https://github.com/images/error/other_user_happy.gif",
                "gravatar_id": "",
                "url": "https://api.github.com/users/other_user",
                "html_url": "https://github.com/other_user",
                "followers_url": "https://api.github.com/users/other_user/followers",
                "following_url": "https://api.github.com/users/other_user/following{/other_user}",
                "gists_url": "https://api.github.com/users/other_user/gists{/gist_id}",
                "starred_url": "https://api.github.com/users/other_user/starred{/owner}{/repo}",
                "subscriptions_url": "https://api.github.com/users/other_user/subscriptions",
                "organizations_url": "https://api.github.com/users/other_user/orgs",
                "repos_url": "https://api.github.com/users/other_user/repos",
                "events_url": "https://api.github.com/users/other_user/events{/privacy}",
                "received_events_url": "https://api.github.com/users/other_user/received_events",
                "type": "User",
                "site_admin": false
            },
            "team_count": 2,
            "invitation_teams_url": "https://api.github.com/organizations/2/invitations/1/teams",
            "invitation_source": "member"
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