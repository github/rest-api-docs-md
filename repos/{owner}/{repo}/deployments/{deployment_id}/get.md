# Get a deployment

`get /repos/{owner}/{repo}/deployments/{deployment_id}`



## Operation Object

```json
{
    "summary": "Get a deployment",
    "description": "",
    "tags": [
        "repos"
    ],
    "operationId": "repos/get-deployment",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/deployments/deployments#get-a-deployment"
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
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/deployment"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/deployment"
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
        "subcategory": "deployments"
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

### `#/components/schemas/deployment`

```json
{
    "title": "Deployment",
    "description": "A request for a specific ref(branch,sha,tag) to be deployed",
    "type": "object",
    "properties": {
        "url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/repos/octocat/example/deployments/1"
        },
        "id": {
            "description": "Unique identifier of the deployment",
            "type": "integer",
            "format": "int64",
            "example": 42
        },
        "node_id": {
            "type": "string",
            "example": "MDEwOkRlcGxveW1lbnQx"
        },
        "sha": {
            "type": "string",
            "example": "a84d88e7554fc1fa21bcbc4efae3c782a70d2b9d"
        },
        "ref": {
            "description": "The ref to deploy. This can be a branch, tag, or sha.",
            "example": "topic-branch",
            "type": "string"
        },
        "task": {
            "description": "Parameter to specify a task to execute",
            "example": "deploy",
            "type": "string"
        },
        "payload": {
            "oneOf": [
                {
                    "type": "object",
                    "additionalProperties": true
                },
                {
                    "type": "string"
                }
            ]
        },
        "original_environment": {
            "type": "string",
            "example": "staging"
        },
        "environment": {
            "description": "Name for the target deployment environment.",
            "example": "production",
            "type": "string"
        },
        "description": {
            "type": "string",
            "example": "Deploy request from hubot",
            "nullable": true
        },
        "creator": {
            "$ref": "#/components/schemas/nullable-simple-user"
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
        "statuses_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/repos/octocat/example/deployments/1/statuses"
        },
        "repository_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/repos/octocat/example"
        },
        "transient_environment": {
            "description": "Specifies if the given environment is will no longer exist at some point in the future. Default: false.",
            "example": true,
            "type": "boolean"
        },
        "production_environment": {
            "description": "Specifies if the given environment is one that end-users directly interact with. Default: false.",
            "example": true,
            "type": "boolean"
        },
        "performed_via_github_app": {
            "$ref": "#/components/schemas/nullable-integration"
        }
    },
    "required": [
        "id",
        "node_id",
        "sha",
        "ref",
        "task",
        "environment",
        "creator",
        "payload",
        "description",
        "statuses_url",
        "repository_url",
        "url",
        "created_at",
        "updated_at"
    ]
}
```

### `#/components/examples/deployment`

```json
{
    "value": {
        "url": "https://api.github.com/repos/octocat/example/deployments/1",
        "id": 1,
        "node_id": "MDEwOkRlcGxveW1lbnQx",
        "sha": "a84d88e7554fc1fa21bcbc4efae3c782a70d2b9d",
        "ref": "topic-branch",
        "task": "deploy",
        "payload": {},
        "original_environment": "staging",
        "environment": "production",
        "description": "Deploy request from hubot",
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
        "created_at": "2012-07-20T01:19:13Z",
        "updated_at": "2012-07-20T01:19:13Z",
        "statuses_url": "https://api.github.com/repos/octocat/example/deployments/1/statuses",
        "repository_url": "https://api.github.com/repos/octocat/example",
        "transient_environment": false,
        "production_environment": true
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