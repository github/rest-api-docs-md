# Get the review history for a workflow run

Anyone with read access to the repository can use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint with a private repository.

## Operation Object

```json
{
    "summary": "Get the review history for a workflow run",
    "description": "Anyone with read access to the repository can use this endpoint.\n\nOAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint with a private repository.",
    "tags": [
        "actions"
    ],
    "operationId": "actions/get-reviews-for-run",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/actions/workflow-runs#get-the-review-history-for-a-workflow-run"
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
                            "$ref": "#/components/schemas/environment-approvals"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/environment-approvals-items"
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

### `#/components/schemas/environment-approvals`

```json
{
    "title": "Environment Approval",
    "description": "An entry in the reviews log for environment deployments",
    "type": "object",
    "properties": {
        "environments": {
            "description": "The list of environments that were approved or rejected",
            "type": "array",
            "items": {
                "type": "object",
                "properties": {
                    "id": {
                        "description": "The id of the environment.",
                        "example": 56780428,
                        "type": "integer"
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
                    },
                    "created_at": {
                        "description": "The time that the environment was created, in ISO 8601 format.",
                        "example": "2020-11-23T22:00:40Z",
                        "format": "date-time",
                        "type": "string"
                    },
                    "updated_at": {
                        "description": "The time that the environment was last updated, in ISO 8601 format.",
                        "example": "2020-11-23T22:00:40Z",
                        "format": "date-time",
                        "type": "string"
                    }
                }
            }
        },
        "state": {
            "description": "Whether deployment to the environment(s) was approved or rejected or pending (with comments)",
            "enum": [
                "approved",
                "rejected",
                "pending"
            ],
            "example": "approved",
            "type": "string"
        },
        "user": {
            "$ref": "#/components/schemas/simple-user"
        },
        "comment": {
            "type": "string",
            "description": "The comment submitted with the deployment review",
            "example": "Ship it!"
        }
    },
    "required": [
        "environments",
        "state",
        "user",
        "comment"
    ]
}
```

### `#/components/examples/environment-approvals-items`

```json
{
    "value": [
        {
            "state": "approved",
            "comment": "Ship it!",
            "environments": [
                {
                    "id": 161088068,
                    "node_id": "MDExOkVudmlyb25tZW50MTYxMDg4MDY4",
                    "name": "staging",
                    "url": "https://api.github.com/repos/github/hello-world/environments/staging",
                    "html_url": "https://github.com/github/hello-world/deployments/activity_log?environments_filter=staging",
                    "created_at": "2020-11-23T22:00:40Z",
                    "updated_at": "2020-11-23T22:00:40Z"
                }
            ],
            "user": {
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
        }
    ]
}
```