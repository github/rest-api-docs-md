# Get Copilot seat assignment details for a user

`get /orgs/{org}/members/{username}/copilot`

**Note**: This endpoint is in beta and is subject to change.

Gets the GitHub Copilot seat assignment details for a member of an organization who currently has access to GitHub Copilot.

Only organization owners can view Copilot seat assignment details for members of their organization.

OAuth app tokens and personal access tokens (classic) need either the `manage_billing:copilot` or `read:org` scopes to use this endpoint.

## Operation Object

```json
{
    "summary": "Get Copilot seat assignment details for a user",
    "description": "**Note**: This endpoint is in beta and is subject to change.\n\nGets the GitHub Copilot seat assignment details for a member of an organization who currently has access to GitHub Copilot.\n\nOnly organization owners can view Copilot seat assignment details for members of their organization.\n\nOAuth app tokens and personal access tokens (classic) need either the `manage_billing:copilot` or `read:org` scopes to use this endpoint.",
    "tags": [
        "copilot"
    ],
    "operationId": "copilot/get-copilot-seat-details-for-user",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/copilot/copilot-user-management#get-copilot-seat-assignment-details-for-a-user"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/org"
        },
        {
            "$ref": "#/components/parameters/username"
        }
    ],
    "responses": {
        "200": {
            "description": "The user's GitHub Copilot seat details, including usage.",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/copilot-seat-details"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/copilot-seat-detail-active"
                        }
                    }
                }
            }
        },
        "500": {
            "$ref": "#/components/responses/internal_error"
        },
        "401": {
            "$ref": "#/components/responses/requires_authentication"
        },
        "403": {
            "$ref": "#/components/responses/forbidden"
        },
        "404": {
            "$ref": "#/components/responses/not_found"
        },
        "422": {
            "description": "Copilot Business or Enterprise is not enabled for this organization or the user has a pending organization invitation."
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "copilot",
        "subcategory": "copilot-user-management"
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

### `#/components/schemas/copilot-seat-details`

```json
{
    "title": "Copilot Business Seat Detail",
    "description": "Information about a Copilot Business seat assignment for a user, team, or organization.",
    "type": "object",
    "properties": {
        "assignee": {
            "type": "object",
            "description": "The assignee that has been granted access to GitHub Copilot.",
            "additionalProperties": true,
            "oneOf": [
                {
                    "$ref": "#/components/schemas/simple-user"
                },
                {
                    "$ref": "#/components/schemas/team"
                },
                {
                    "$ref": "#/components/schemas/organization"
                }
            ]
        },
        "organization": {
            "type": "object",
            "description": "The organization to which this seat belongs.",
            "nullable": true,
            "oneOf": [
                {
                    "$ref": "#/components/schemas/organization-simple"
                }
            ]
        },
        "assigning_team": {
            "description": "The team through which the assignee is granted access to GitHub Copilot, if applicable.",
            "oneOf": [
                {
                    "$ref": "#/components/schemas/team"
                },
                {
                    "$ref": "#/components/schemas/enterprise-team"
                }
            ],
            "nullable": true
        },
        "pending_cancellation_date": {
            "type": "string",
            "format": "date",
            "nullable": true,
            "description": "The pending cancellation date for the seat, in `YYYY-MM-DD` format. This will be null unless the assignee's Copilot access has been canceled during the current billing cycle. If the seat has been cancelled, this corresponds to the start of the organization's next billing cycle."
        },
        "last_activity_at": {
            "type": "string",
            "format": "date-time",
            "nullable": true,
            "description": "Timestamp of user's last GitHub Copilot activity, in ISO 8601 format."
        },
        "last_activity_editor": {
            "type": "string",
            "nullable": true,
            "description": "Last editor that was used by the user for a GitHub Copilot completion."
        },
        "created_at": {
            "type": "string",
            "format": "date-time",
            "description": "Timestamp of when the assignee was last granted access to GitHub Copilot, in ISO 8601 format."
        },
        "updated_at": {
            "type": "string",
            "format": "date-time",
            "description": "Timestamp of when the assignee's GitHub Copilot access was last updated, in ISO 8601 format."
        }
    },
    "required": [
        "assignee",
        "created_at"
    ],
    "additionalProperties": false
}
```

### `#/components/examples/copilot-seat-detail-active`

```json
{
    "value": {
        "created_at": "2021-08-03T18:00:00-06:00",
        "updated_at": "2021-09-23T15:00:00-06:00",
        "pending_cancellation_date": null,
        "last_activity_at": "2021-10-14T00:53:32-06:00",
        "last_activity_editor": "vscode/1.77.3/copilot/1.86.82",
        "assignee": {
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
        "assigning_team": {
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
    }
}
```

### `#/components/responses/internal_error`

```json
{
    "description": "Internal Error",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/basic-error"
            }
        }
    }
}
```

### `#/components/responses/requires_authentication`

```json
{
    "description": "Requires authentication",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/basic-error"
            }
        }
    }
}
```

### `#/components/responses/forbidden`

```json
{
    "description": "Forbidden",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/basic-error"
            }
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