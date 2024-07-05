# List all Copilot seat assignments for an organization

**Note**: This endpoint is in beta and is subject to change.

Lists all active Copilot seats for an organization with a Copilot Business or Copilot Enterprise subscription.
Only organization owners can view assigned seats.

OAuth app tokens and personal access tokens (classic) need either the `manage_billing:copilot` or `read:org` scopes to use this endpoint.

## Operation Object

```json
{
    "summary": "List all Copilot seat assignments for an organization",
    "description": "**Note**: This endpoint is in beta and is subject to change.\n\nLists all active Copilot seats for an organization with a Copilot Business or Copilot Enterprise subscription.\nOnly organization owners can view assigned seats.\n\nOAuth app tokens and personal access tokens (classic) need either the `manage_billing:copilot` or `read:org` scopes to use this endpoint.",
    "tags": [
        "copilot"
    ],
    "operationId": "copilot/list-copilot-seats",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/copilot/copilot-user-management#list-all-copilot-seat-assignments-for-an-organization"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/org"
        },
        {
            "$ref": "#/components/parameters/page"
        },
        {
            "name": "per_page",
            "description": "The number of results per page (max 100). For more information, see \"[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api).\"",
            "in": "query",
            "schema": {
                "type": "integer",
                "default": 50
            }
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "type": "object",
                        "properties": {
                            "total_seats": {
                                "type": "integer",
                                "description": "Total number of Copilot seats for the organization currently being billed."
                            },
                            "seats": {
                                "type": "array",
                                "items": {
                                    "$ref": "#/components/schemas/copilot-seat-details"
                                }
                            }
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/copilot-seats-list"
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

### `#/components/examples/copilot-seats-list`

```json
{
    "value": {
        "total_seats": 2,
        "seats": [
            {
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
            },
            {
                "created_at": "2021-09-23T18:00:00-06:00",
                "updated_at": "2021-09-23T15:00:00-06:00",
                "pending_cancellation_date": "2021-11-01",
                "last_activity_at": "2021-10-13T00:53:32-06:00",
                "last_activity_editor": "vscode/1.77.3/copilot/1.86.82",
                "assignee": {
                    "login": "octokitten",
                    "id": 1,
                    "node_id": "MDQ76VNlcjE=",
                    "avatar_url": "https://github.com/images/error/octokitten_happy.gif",
                    "gravatar_id": "",
                    "url": "https://api.github.com/users/octokitten",
                    "html_url": "https://github.com/octokitten",
                    "followers_url": "https://api.github.com/users/octokitten/followers",
                    "following_url": "https://api.github.com/users/octokitten/following{/other_user}",
                    "gists_url": "https://api.github.com/users/octokitten/gists{/gist_id}",
                    "starred_url": "https://api.github.com/users/octokitten/starred{/owner}{/repo}",
                    "subscriptions_url": "https://api.github.com/users/octokitten/subscriptions",
                    "organizations_url": "https://api.github.com/users/octokitten/orgs",
                    "repos_url": "https://api.github.com/users/octokitten/repos",
                    "events_url": "https://api.github.com/users/octokitten/events{/privacy}",
                    "received_events_url": "https://api.github.com/users/octokitten/received_events",
                    "type": "User",
                    "site_admin": false
                }
            }
        ]
    }
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