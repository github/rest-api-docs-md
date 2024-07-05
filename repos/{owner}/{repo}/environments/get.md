# List environments

`get /repos/{owner}/{repo}/environments`

Lists the environments for a repository.

Anyone with read access to the repository can use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint with a private repository.

## Operation Object

```json
{
    "summary": "List environments",
    "description": "Lists the environments for a repository.\n\nAnyone with read access to the repository can use this endpoint.\n\nOAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint with a private repository.",
    "tags": [
        "repos"
    ],
    "operationId": "repos/get-all-environments",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/deployments/environments#list-environments"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
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
                        "type": "object",
                        "properties": {
                            "total_count": {
                                "description": "The number of environments in this repository",
                                "example": 5,
                                "type": "integer"
                            },
                            "environments": {
                                "type": "array",
                                "items": {
                                    "$ref": "#/components/schemas/environment"
                                }
                            }
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/environments"
                        }
                    }
                }
            }
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "deployments",
        "subcategory": "environments"
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

### `#/components/schemas/environment`

```json
{
    "title": "Environment",
    "description": "Details of a deployment environment",
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
        },
        "protection_rules": {
            "type": "array",
            "description": "Built-in deployment protection rules for the environment.",
            "items": {
                "anyOf": [
                    {
                        "type": "object",
                        "properties": {
                            "id": {
                                "type": "integer",
                                "example": 3515
                            },
                            "node_id": {
                                "type": "string",
                                "example": "MDQ6R2F0ZTM1MTU="
                            },
                            "type": {
                                "type": "string",
                                "example": "wait_timer"
                            },
                            "wait_timer": {
                                "$ref": "#/components/schemas/wait-timer"
                            }
                        },
                        "required": [
                            "id",
                            "node_id",
                            "type"
                        ]
                    },
                    {
                        "type": "object",
                        "properties": {
                            "id": {
                                "type": "integer",
                                "example": 3755
                            },
                            "node_id": {
                                "type": "string",
                                "example": "MDQ6R2F0ZTM3NTU="
                            },
                            "prevent_self_review": {
                                "type": "boolean",
                                "example": false,
                                "description": "Whether deployments to this environment can be approved by the user who created the deployment."
                            },
                            "type": {
                                "type": "string",
                                "example": "required_reviewers"
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
                            "id",
                            "node_id",
                            "type"
                        ]
                    },
                    {
                        "type": "object",
                        "properties": {
                            "id": {
                                "type": "integer",
                                "example": 3515
                            },
                            "node_id": {
                                "type": "string",
                                "example": "MDQ6R2F0ZTM1MTU="
                            },
                            "type": {
                                "type": "string",
                                "example": "branch_policy"
                            }
                        },
                        "required": [
                            "id",
                            "node_id",
                            "type"
                        ]
                    }
                ]
            }
        },
        "deployment_branch_policy": {
            "$ref": "#/components/schemas/deployment-branch-policy-settings"
        }
    },
    "required": [
        "id",
        "node_id",
        "name",
        "url",
        "html_url",
        "created_at",
        "updated_at"
    ]
}
```

### `#/components/examples/environments`

```json
{
    "value": {
        "total_count": 1,
        "environments": [
            {
                "id": 161088068,
                "node_id": "MDExOkVudmlyb25tZW50MTYxMDg4MDY4",
                "name": "staging",
                "url": "https://api.github.com/repos/github/hello-world/environments/staging",
                "html_url": "https://github.com/github/hello-world/deployments/activity_log?environments_filter=staging",
                "created_at": "2020-11-23T22:00:40Z",
                "updated_at": "2020-11-23T22:00:40Z",
                "protection_rules": [
                    {
                        "id": 3736,
                        "node_id": "MDQ6R2F0ZTM3MzY=",
                        "type": "wait_timer",
                        "wait_timer": 30
                    },
                    {
                        "id": 3755,
                        "node_id": "MDQ6R2F0ZTM3NTU=",
                        "prevent_self_review": false,
                        "type": "required_reviewers",
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
                    },
                    {
                        "id": 3756,
                        "node_id": "MDQ6R2F0ZTM3NTY=",
                        "type": "branch_policy"
                    }
                ],
                "deployment_branch_policy": {
                    "protected_branches": false,
                    "custom_branch_policies": true
                }
            }
        ]
    }
}
```