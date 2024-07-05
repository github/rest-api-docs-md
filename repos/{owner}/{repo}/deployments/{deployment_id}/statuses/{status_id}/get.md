# Get a deployment status

`get /repos/{owner}/{repo}/deployments/{deployment_id}/statuses/{status_id}`

Users with pull access can view a deployment status for a deployment:

## Operation Object

```json
{
    "summary": "Get a deployment status",
    "description": "Users with pull access can view a deployment status for a deployment:",
    "tags": [
        "repos"
    ],
    "operationId": "repos/get-deployment-status",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/deployments/statuses#get-a-deployment-status"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "$ref": "#/components/parameters/deployment-id"
        },
        {
            "name": "status_id",
            "in": "path",
            "required": true,
            "schema": {
                "type": "integer"
            }
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/deployment-status"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/deployment-status"
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
        "category": "deployments",
        "subcategory": "statuses"
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

### `#/components/parameters/deployment-id`

```json
{
    "name": "deployment_id",
    "description": "deployment_id parameter",
    "in": "path",
    "required": true,
    "schema": {
        "type": "integer"
    }
}
```

### `#/components/schemas/deployment-status`

```json
{
    "title": "Deployment Status",
    "description": "The status of a deployment.",
    "type": "object",
    "properties": {
        "url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/repos/octocat/example/deployments/42/statuses/1"
        },
        "id": {
            "type": "integer",
            "format": "int64",
            "example": 1
        },
        "node_id": {
            "type": "string",
            "example": "MDE2OkRlcGxveW1lbnRTdGF0dXMx"
        },
        "state": {
            "description": "The state of the status.",
            "enum": [
                "error",
                "failure",
                "inactive",
                "pending",
                "success",
                "queued",
                "in_progress"
            ],
            "example": "success",
            "type": "string"
        },
        "creator": {
            "$ref": "#/components/schemas/nullable-simple-user"
        },
        "description": {
            "description": "A short description of the status.",
            "default": "",
            "type": "string",
            "maxLength": 140,
            "example": "Deployment finished successfully."
        },
        "environment": {
            "description": "The environment of the deployment that the status is for.",
            "default": "",
            "type": "string",
            "example": "production"
        },
        "target_url": {
            "description": "Deprecated: the URL to associate with this status.",
            "default": "",
            "type": "string",
            "format": "uri",
            "example": "https://example.com/deployment/42/output"
        },
        "created_at": {
            "type": "string",
            "format": "date-time",
            "example": "2012-07-20T01:19:13Z"
        },
        "updated_at": {
            "type": "string",
            "format": "date-time",
            "example": "2012-07-20T01:19:13Z"
        },
        "deployment_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/repos/octocat/example/deployments/42"
        },
        "repository_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/repos/octocat/example"
        },
        "environment_url": {
            "description": "The URL for accessing your environment.",
            "default": "",
            "type": "string",
            "format": "uri",
            "example": "https://staging.example.com/"
        },
        "log_url": {
            "description": "The URL to associate with this status.",
            "default": "",
            "type": "string",
            "format": "uri",
            "example": "https://example.com/deployment/42/output"
        },
        "performed_via_github_app": {
            "$ref": "#/components/schemas/nullable-integration"
        }
    },
    "required": [
        "id",
        "node_id",
        "state",
        "creator",
        "description",
        "deployment_url",
        "target_url",
        "repository_url",
        "url",
        "created_at",
        "updated_at"
    ]
}
```

### `#/components/examples/deployment-status`

```json
{
    "value": {
        "url": "https://api.github.com/repos/octocat/example/deployments/42/statuses/1",
        "id": 1,
        "node_id": "MDE2OkRlcGxveW1lbnRTdGF0dXMx",
        "state": "success",
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
        "description": "Deployment finished successfully.",
        "environment": "production",
        "target_url": "https://example.com/deployment/42/output",
        "created_at": "2012-07-20T01:19:13Z",
        "updated_at": "2012-07-20T01:19:13Z",
        "deployment_url": "https://api.github.com/repos/octocat/example/deployments/42",
        "repository_url": "https://api.github.com/repos/octocat/example",
        "environment_url": "https://test-branch.lab.acme.com",
        "log_url": "https://example.com/deployment/42/output"
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