# Get a check run

Gets a single check run using its `id`.

**Note:** The Checks API only looks for pushes in the repository where the check suite or check run were created. Pushes to a branch in a forked repository are not detected and return an empty `pull_requests` array.

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint on a private repository.

## Operation Object

```json
{
    "summary": "Get a check run",
    "description": "Gets a single check run using its `id`.\n\n**Note:** The Checks API only looks for pushes in the repository where the check suite or check run were created. Pushes to a branch in a forked repository are not detected and return an empty `pull_requests` array.\n\nOAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint on a private repository.",
    "tags": [
        "checks"
    ],
    "operationId": "checks/get",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/checks/runs#get-a-check-run"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "$ref": "#/components/parameters/check-run-id"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/check-run"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/check-run"
                        }
                    }
                }
            }
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "checks",
        "subcategory": "runs"
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

### `#/components/parameters/check-run-id`

```json
{
    "name": "check_run_id",
    "description": "The unique identifier of the check run.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "integer"
    }
}
```

### `#/components/schemas/check-run`

```json
{
    "title": "CheckRun",
    "description": "A check performed on the code of a given code change",
    "type": "object",
    "properties": {
        "id": {
            "description": "The id of the check.",
            "example": 21,
            "type": "integer"
        },
        "head_sha": {
            "description": "The SHA of the commit that is being checked.",
            "example": "009b8a3a9ccbb128af87f9b1c0f4c62e8a304f6d",
            "type": "string"
        },
        "node_id": {
            "type": "string",
            "example": "MDg6Q2hlY2tSdW40"
        },
        "external_id": {
            "type": "string",
            "example": "42",
            "nullable": true
        },
        "url": {
            "type": "string",
            "example": "https://api.github.com/repos/github/hello-world/check-runs/4"
        },
        "html_url": {
            "type": "string",
            "example": "https://github.com/github/hello-world/runs/4",
            "nullable": true
        },
        "details_url": {
            "type": "string",
            "example": "https://example.com",
            "nullable": true
        },
        "status": {
            "description": "The phase of the lifecycle that the check is currently in. Statuses of waiting, requested, and pending are reserved for GitHub Actions check runs.",
            "example": "queued",
            "type": "string",
            "enum": [
                "queued",
                "in_progress",
                "completed",
                "waiting",
                "requested",
                "pending"
            ]
        },
        "conclusion": {
            "type": "string",
            "example": "neutral",
            "enum": [
                "success",
                "failure",
                "neutral",
                "cancelled",
                "skipped",
                "timed_out",
                "action_required"
            ],
            "nullable": true
        },
        "started_at": {
            "type": "string",
            "format": "date-time",
            "example": "2018-05-04T01:14:52Z",
            "nullable": true
        },
        "completed_at": {
            "type": "string",
            "format": "date-time",
            "example": "2018-05-04T01:14:52Z",
            "nullable": true
        },
        "output": {
            "type": "object",
            "properties": {
                "title": {
                    "type": "string",
                    "nullable": true
                },
                "summary": {
                    "type": "string",
                    "nullable": true
                },
                "text": {
                    "type": "string",
                    "nullable": true
                },
                "annotations_count": {
                    "type": "integer"
                },
                "annotations_url": {
                    "type": "string",
                    "format": "uri"
                }
            },
            "required": [
                "title",
                "summary",
                "text",
                "annotations_count",
                "annotations_url"
            ]
        },
        "name": {
            "description": "The name of the check.",
            "example": "test-coverage",
            "type": "string"
        },
        "check_suite": {
            "type": "object",
            "properties": {
                "id": {
                    "type": "integer"
                }
            },
            "required": [
                "id"
            ],
            "nullable": true
        },
        "app": {
            "$ref": "#/components/schemas/nullable-integration"
        },
        "pull_requests": {
            "description": "Pull requests that are open with a `head_sha` or `head_branch` that matches the check. The returned pull requests do not necessarily indicate pull requests that triggered the check.",
            "type": "array",
            "items": {
                "$ref": "#/components/schemas/pull-request-minimal"
            }
        },
        "deployment": {
            "$ref": "#/components/schemas/deployment-simple"
        }
    },
    "required": [
        "id",
        "node_id",
        "head_sha",
        "name",
        "url",
        "html_url",
        "details_url",
        "status",
        "conclusion",
        "started_at",
        "completed_at",
        "external_id",
        "check_suite",
        "output",
        "app",
        "pull_requests"
    ]
}
```

### `#/components/examples/check-run`

```json
{
    "value": {
        "id": 4,
        "head_sha": "ce587453ced02b1526dfb4cb910479d431683101",
        "node_id": "MDg6Q2hlY2tSdW40",
        "external_id": "",
        "url": "https://api.github.com/repos/github/hello-world/check-runs/4",
        "html_url": "https://github.com/github/hello-world/runs/4",
        "details_url": "https://example.com",
        "status": "completed",
        "conclusion": "neutral",
        "started_at": "2018-05-04T01:14:52Z",
        "completed_at": "2018-05-04T01:14:52Z",
        "output": {
            "title": "Mighty Readme report",
            "summary": "There are 0 failures, 2 warnings, and 1 notice.",
            "text": "You may have some misspelled words on lines 2 and 4. You also may want to add a section in your README about how to install your app.",
            "annotations_count": 2,
            "annotations_url": "https://api.github.com/repos/github/hello-world/check-runs/4/annotations"
        },
        "name": "mighty_readme",
        "check_suite": {
            "id": 5
        },
        "app": {
            "id": 1,
            "slug": "octoapp",
            "node_id": "MDExOkludGVncmF0aW9uMQ==",
            "owner": {
                "login": "github",
                "id": 1,
                "node_id": "MDEyOk9yZ2FuaXphdGlvbjE=",
                "url": "https://api.github.com/orgs/github",
                "repos_url": "https://api.github.com/orgs/github/repos",
                "events_url": "https://api.github.com/orgs/github/events",
                "avatar_url": "https://github.com/images/error/octocat_happy.gif",
                "gravatar_id": "",
                "html_url": "https://github.com/octocat",
                "followers_url": "https://api.github.com/users/octocat/followers",
                "following_url": "https://api.github.com/users/octocat/following{/other_user}",
                "gists_url": "https://api.github.com/users/octocat/gists{/gist_id}",
                "starred_url": "https://api.github.com/users/octocat/starred{/owner}{/repo}",
                "subscriptions_url": "https://api.github.com/users/octocat/subscriptions",
                "organizations_url": "https://api.github.com/users/octocat/orgs",
                "received_events_url": "https://api.github.com/users/octocat/received_events",
                "type": "User",
                "site_admin": true
            },
            "name": "Octocat App",
            "description": "",
            "external_url": "https://example.com",
            "html_url": "https://github.com/apps/octoapp",
            "created_at": "2017-07-08T16:18:44-04:00",
            "updated_at": "2017-07-08T16:18:44-04:00",
            "permissions": {
                "metadata": "read",
                "contents": "read",
                "issues": "write",
                "single_file": "write"
            },
            "events": [
                "push",
                "pull_request"
            ]
        },
        "pull_requests": [
            {
                "url": "https://api.github.com/repos/github/hello-world/pulls/1",
                "id": 1934,
                "number": 3956,
                "head": {
                    "ref": "say-hello",
                    "sha": "3dca65fa3e8d4b3da3f3d056c59aee1c50f41390",
                    "repo": {
                        "id": 526,
                        "url": "https://api.github.com/repos/github/hello-world",
                        "name": "hello-world"
                    }
                },
                "base": {
                    "ref": "master",
                    "sha": "e7fdf7640066d71ad16a86fbcbb9c6a10a18af4f",
                    "repo": {
                        "id": 526,
                        "url": "https://api.github.com/repos/github/hello-world",
                        "name": "hello-world"
                    }
                }
            }
        ]
    }
}
```