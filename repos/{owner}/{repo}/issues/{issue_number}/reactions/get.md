# List reactions for an issue

List the reactions to an [issue](https://docs.github.com/rest/issues/issues#get-an-issue).

## Operation Object

```json
{
    "summary": "List reactions for an issue",
    "description": "List the reactions to an [issue](https://docs.github.com/rest/issues/issues#get-an-issue).",
    "tags": [
        "reactions"
    ],
    "operationId": "reactions/list-for-issue",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/reactions/reactions#list-reactions-for-an-issue"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "$ref": "#/components/parameters/issue-number"
        },
        {
            "name": "content",
            "description": "Returns a single [reaction type](https://docs.github.com/rest/reactions/reactions#about-reactions). Omit this parameter to list all reactions to an issue.",
            "in": "query",
            "required": false,
            "schema": {
                "type": "string",
                "enum": [
                    "+1",
                    "-1",
                    "laugh",
                    "confused",
                    "heart",
                    "hooray",
                    "rocket",
                    "eyes"
                ]
            }
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
                            "$ref": "#/components/schemas/reaction"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/reaction-items"
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
        "404": {
            "$ref": "#/components/responses/not_found"
        },
        "410": {
            "$ref": "#/components/responses/gone"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "reactions",
        "subcategory": "reactions"
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

### `#/components/parameters/issue-number`

```json
{
    "name": "issue_number",
    "description": "The number that identifies the issue.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "integer"
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

### `#/components/schemas/reaction`

```json
{
    "title": "Reaction",
    "description": "Reactions to conversations provide a way to help people express their feelings more simply and effectively.",
    "type": "object",
    "properties": {
        "id": {
            "type": "integer",
            "example": 1
        },
        "node_id": {
            "type": "string",
            "example": "MDg6UmVhY3Rpb24x"
        },
        "user": {
            "$ref": "#/components/schemas/nullable-simple-user"
        },
        "content": {
            "description": "The reaction to use",
            "example": "heart",
            "type": "string",
            "enum": [
                "+1",
                "-1",
                "laugh",
                "confused",
                "heart",
                "hooray",
                "rocket",
                "eyes"
            ]
        },
        "created_at": {
            "type": "string",
            "format": "date-time",
            "example": "2016-05-20T20:09:31Z"
        }
    },
    "required": [
        "id",
        "node_id",
        "user",
        "content",
        "created_at"
    ]
}
```

### `#/components/examples/reaction-items`

```json
{
    "value": [
        {
            "id": 1,
            "node_id": "MDg6UmVhY3Rpb24x",
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
            "content": "heart",
            "created_at": "2016-05-20T20:09:31Z"
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

### `#/components/responses/gone`

```json
{
    "description": "Gone",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/basic-error"
            }
        }
    }
}
```