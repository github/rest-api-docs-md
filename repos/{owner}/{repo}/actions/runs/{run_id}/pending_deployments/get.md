# Get pending deployments for a workflow run

Get all deployment environments for a workflow run that are waiting for protection rules to pass.

Anyone with read access to the repository can use this endpoint.

If the repository is private, OAuth tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "Get pending deployments for a workflow run",
    "description": "Get all deployment environments for a workflow run that are waiting for protection rules to pass.\n\nAnyone with read access to the repository can use this endpoint.\n\nIf the repository is private, OAuth tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.",
    "tags": [
        "actions"
    ],
    "operationId": "actions/get-pending-deployments-for-run",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/actions/workflow-runs#get-pending-deployments-for-a-workflow-run"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "$ref": "#/components/parameters/run-id"
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
                            "$ref": "#/components/schemas/pending-deployment"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/pending-deployment-items"
                        }
                    }
                }
            }
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "actions",
        "subcategory": "workflow-runs"
    }
}
```

## References

### `#/components/parameters/owner`

```json
{
    "name": "owner",
    "description": "The account owner of the repository. The name is not case sensitive.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "string"
    }
}
```

### `#/components/parameters/repo`

```json
{
    "name": "repo",
    "description": "The name of the repository without the `.git` extension. The name is not case sensitive.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "string"
    }
}
```

### `#/components/parameters/run-id`

```json
{
    "name": "run_id",
    "description": "The unique identifier of the workflow run.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "integer"
    }
}
```

### `#/components/schemas/pending-deployment`

```json
{
    "title": "Pending Deployment",
    "description": "Details of a deployment that is waiting for protection rules to pass",
    "type": "object",
    "properties": {
        "environment": {
            "type": "object",
            "properties": {
                "id": {
                    "description": "The id of the environment.",
                    "type": "integer",
                    "format": "int64",
                    "example": 56780428
                },
                "node_id": {
                    "type": "string",
                    "example": "MDExOkVudmlyb25tZW50NTY3ODA0Mjg="
                },
                "name": {
                    "description": "The name of the environment.",
                    "example": "staging",
                    "type": "string"
                },
                "url": {
                    "type": "string",
                    "example": "https://api.github.com/repos/github/hello-world/environments/staging"
                },
                "html_url": {
                    "type": "string",
                    "example": "https://github.com/github/hello-world/deployments/activity_log?environments_filter=staging"
                }
            }
        },
        "wait_timer": {
            "type": "integer",
            "description": "The set duration of the wait timer",
            "example": 30
        },
        "wait_timer_started_at": {
            "description": "The time that the wait timer began.",
            "example": "2020-11-23T22:00:40Z",
            "format": "date-time",
            "type": "string",
            "nullable": true
        },
        "current_user_can_approve": {
            "description": "Whether the currently authenticated user can approve the deployment",
            "type": "boolean",
            "example": true
        },
        "reviewers": {
            "type": "array",
            "description": "The people or teams that may approve jobs that reference the environment. You can list up to six users or teams as reviewers. The reviewers must have at least read access to the repository. Only one of the required reviewers needs to approve the job for it to proceed.",
            "items": {
                "type": "object",
                "properties": {
                    "type": {
                        "$ref": "#/components/schemas/deployment-reviewer-type"
                    },
                    "reviewer": {
                        "anyOf": [
                            {
                                "$ref": "#/components/schemas/simple-user"
                            },
                            {
                                "$ref": "#/components/schemas/team"
                            }
                        ]
                    }
                }
            }
        }
    },
    "required": [
        "environment",
        "wait_timer",
        "wait_timer_started_at",
        "current_user_can_approve",
        "reviewers"
    ]
}
```

### `#/components/examples/pending-deployment-items`

```json
{
    "value": [
        {
            "environment": {
                "id": 161088068,
                "node_id": "MDExOkVudmlyb25tZW50MTYxMDg4MDY4",
                "name": "staging",
                "url": "https://api.github.com/repos/github/hello-world/environments/staging",
                "html_url": "https://github.com/github/hello-world/deployments/activity_log?environments_filter=staging"
            },
            "wait_timer": 30,
            "wait_timer_started_at": "2020-11-23T22:00:40Z",
            "current_user_can_approve": true,
            "reviewers": [
                {
                    "type": "User",
                    "reviewer": {
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
                    }
                },
                {
                    "type": "Team",
                    "reviewer": {
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
            ]
        }
    ]
}
```