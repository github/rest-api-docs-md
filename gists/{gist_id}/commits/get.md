# List gist commits



## Operation Object

```json
{
    "summary": "List gist commits",
    "description": "",
    "tags": [
        "gists"
    ],
    "operationId": "gists/list-commits",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/gists/gists#list-gist-commits"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/gist-id"
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
                            "$ref": "#/components/schemas/gist-commit"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/gist-commit-items"
                        }
                    }
                }
            },
            "headers": {
                "Link": {
                    "example": "<https://api.github.com/resource?page=2>; rel=\"next\"",
                    "schema": {
                        "type": "string"
                    }
                }
            }
        },
        "404": {
            "$ref": "#/components/responses/not_found"
        },
        "304": {
            "$ref": "#/components/responses/not_modified"
        },
        "403": {
            "$ref": "#/components/responses/forbidden"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": false,
        "category": "gists",
        "subcategory": "gists"
    }
}
```

## References

### `#/components/parameters/gist-id`

```json
{
    "name": "gist_id",
    "description": "The unique identifier of the gist.",
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

### `#/components/schemas/gist-commit`

```json
{
    "title": "Gist Commit",
    "description": "Gist Commit",
    "type": "object",
    "properties": {
        "url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/gists/aa5a315d61ae9438b18d/57a7f021a713b1c5a6a199b54cc514735d2d462f"
        },
        "version": {
            "type": "string",
            "example": "57a7f021a713b1c5a6a199b54cc514735d2d462f"
        },
        "user": {
            "$ref": "#/components/schemas/nullable-simple-user"
        },
        "change_status": {
            "type": "object",
            "properties": {
                "total": {
                    "type": "integer"
                },
                "additions": {
                    "type": "integer"
                },
                "deletions": {
                    "type": "integer"
                }
            }
        },
        "committed_at": {
            "type": "string",
            "format": "date-time",
            "example": "2010-04-14T02:15:15Z"
        }
    },
    "required": [
        "url",
        "user",
        "version",
        "committed_at",
        "change_status"
    ]
}
```

### `#/components/examples/gist-commit-items`

```json
{
    "value": [
        {
            "url": "https://api.github.com/gists/aa5a315d61ae9438b18d/57a7f021a713b1c5a6a199b54cc514735d2d462f",
            "version": "57a7f021a713b1c5a6a199b54cc514735d2d462f",
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
            },
            "change_status": {
                "deletions": 0,
                "additions": 180,
                "total": 180
            },
            "committed_at": "2010-04-14T02:15:15Z"
        }
    ]
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

### `#/components/responses/not_modified`

```json
{
    "description": "Not modified"
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