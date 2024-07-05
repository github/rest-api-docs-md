# List commit statuses for a reference

`get /repos/{owner}/{repo}/commits/{ref}/statuses`

Users with pull access in a repository can view commit statuses for a given ref. The ref can be a SHA, a branch name, or a tag name. Statuses are returned in reverse chronological order. The first status in the list will be the latest one.

This resource is also available via a legacy route: `GET /repos/:owner/:repo/statuses/:ref`.

## Operation Object

```json
{
    "summary": "List commit statuses for a reference",
    "description": "Users with pull access in a repository can view commit statuses for a given ref. The ref can be a SHA, a branch name, or a tag name. Statuses are returned in reverse chronological order. The first status in the list will be the latest one.\n\nThis resource is also available via a legacy route: `GET /repos/:owner/:repo/statuses/:ref`.",
    "tags": [
        "repos"
    ],
    "operationId": "repos/list-commit-statuses-for-ref",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/commits/statuses#list-commit-statuses-for-a-reference"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "$ref": "#/components/parameters/commit-ref"
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
                            "$ref": "#/components/schemas/status"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/status-items"
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
        "301": {
            "$ref": "#/components/responses/moved_permanently"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "commits",
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

### `#/components/parameters/commit-ref`

```json
{
    "name": "ref",
    "description": "The commit reference. Can be a commit SHA, branch name (`heads/BRANCH_NAME`), or tag name (`tags/TAG_NAME`). For more information, see \"[Git References](https://git-scm.com/book/en/v2/Git-Internals-Git-References)\" in the Git documentation.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "string"
    },
    "x-multi-segment": true
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

### `#/components/schemas/status`

```json
{
    "title": "Status",
    "description": "The status of a commit.",
    "type": "object",
    "properties": {
        "url": {
            "type": "string"
        },
        "avatar_url": {
            "type": "string",
            "nullable": true
        },
        "id": {
            "type": "integer"
        },
        "node_id": {
            "type": "string"
        },
        "state": {
            "type": "string"
        },
        "description": {
            "type": "string",
            "nullable": true
        },
        "target_url": {
            "type": "string",
            "nullable": true
        },
        "context": {
            "type": "string"
        },
        "created_at": {
            "type": "string"
        },
        "updated_at": {
            "type": "string"
        },
        "creator": {
            "$ref": "#/components/schemas/nullable-simple-user"
        }
    },
    "required": [
        "url",
        "avatar_url",
        "id",
        "node_id",
        "state",
        "description",
        "target_url",
        "context",
        "created_at",
        "updated_at",
        "creator"
    ]
}
```

### `#/components/examples/status-items`

```json
{
    "value": [
        {
            "url": "https://api.github.com/repos/octocat/Hello-World/statuses/6dcb09b5b57875f334f61aebed695e2e4193db5e",
            "avatar_url": "https://github.com/images/error/hubot_happy.gif",
            "id": 1,
            "node_id": "MDY6U3RhdHVzMQ==",
            "state": "success",
            "description": "Build has completed successfully",
            "target_url": "https://ci.example.com/1000/output",
            "context": "continuous-integration/jenkins",
            "created_at": "2012-07-20T01:19:13Z",
            "updated_at": "2012-07-20T01:19:13Z",
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
            }
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

### `#/components/responses/moved_permanently`

```json
{
    "description": "Moved permanently",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/basic-error"
            }
        }
    }
}
```