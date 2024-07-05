# List gist forks

`get /gists/{gist_id}/forks`



## Operation Object

```json
{
    "summary": "List gist forks",
    "description": "",
    "tags": [
        "gists"
    ],
    "operationId": "gists/list-forks",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/gists/gists#list-gist-forks"
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
                            "$ref": "#/components/schemas/gist-simple"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/gist-fork-items"
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

### `#/components/schemas/gist-simple`

```json
{
    "title": "Gist Simple",
    "description": "Gist Simple",
    "type": "object",
    "properties": {
        "forks": {
            "deprecated": true,
            "nullable": true,
            "type": "array",
            "items": {
                "type": "object",
                "properties": {
                    "id": {
                        "type": "string"
                    },
                    "url": {
                        "type": "string",
                        "format": "uri"
                    },
                    "user": {
                        "$ref": "#/components/schemas/public-user"
                    },
                    "created_at": {
                        "type": "string",
                        "format": "date-time"
                    },
                    "updated_at": {
                        "type": "string",
                        "format": "date-time"
                    }
                }
            }
        },
        "history": {
            "deprecated": true,
            "nullable": true,
            "type": "array",
            "items": {
                "$ref": "#/components/schemas/gist-history"
            }
        },
        "fork_of": {
            "nullable": true,
            "title": "Gist",
            "description": "Gist",
            "type": "object",
            "properties": {
                "url": {
                    "type": "string",
                    "format": "uri"
                },
                "forks_url": {
                    "type": "string",
                    "format": "uri"
                },
                "commits_url": {
                    "type": "string",
                    "format": "uri"
                },
                "id": {
                    "type": "string"
                },
                "node_id": {
                    "type": "string"
                },
                "git_pull_url": {
                    "type": "string",
                    "format": "uri"
                },
                "git_push_url": {
                    "type": "string",
                    "format": "uri"
                },
                "html_url": {
                    "type": "string",
                    "format": "uri"
                },
                "files": {
                    "type": "object",
                    "additionalProperties": {
                        "type": "object",
                        "properties": {
                            "filename": {
                                "type": "string"
                            },
                            "type": {
                                "type": "string"
                            },
                            "language": {
                                "type": "string"
                            },
                            "raw_url": {
                                "type": "string"
                            },
                            "size": {
                                "type": "integer"
                            }
                        }
                    }
                },
                "public": {
                    "type": "boolean"
                },
                "created_at": {
                    "type": "string",
                    "format": "date-time"
                },
                "updated_at": {
                    "type": "string",
                    "format": "date-time"
                },
                "description": {
                    "type": "string",
                    "nullable": true
                },
                "comments": {
                    "type": "integer"
                },
                "user": {
                    "$ref": "#/components/schemas/nullable-simple-user"
                },
                "comments_url": {
                    "type": "string",
                    "format": "uri"
                },
                "owner": {
                    "$ref": "#/components/schemas/nullable-simple-user"
                },
                "truncated": {
                    "type": "boolean"
                },
                "forks": {
                    "type": "array",
                    "items": {}
                },
                "history": {
                    "type": "array",
                    "items": {}
                }
            },
            "required": [
                "id",
                "node_id",
                "url",
                "forks_url",
                "commits_url",
                "git_pull_url",
                "git_push_url",
                "html_url",
                "comments_url",
                "public",
                "description",
                "comments",
                "user",
                "files",
                "created_at",
                "updated_at"
            ]
        },
        "url": {
            "type": "string"
        },
        "forks_url": {
            "type": "string"
        },
        "commits_url": {
            "type": "string"
        },
        "id": {
            "type": "string"
        },
        "node_id": {
            "type": "string"
        },
        "git_pull_url": {
            "type": "string"
        },
        "git_push_url": {
            "type": "string"
        },
        "html_url": {
            "type": "string"
        },
        "files": {
            "type": "object",
            "additionalProperties": {
                "nullable": true,
                "type": "object",
                "properties": {
                    "filename": {
                        "type": "string"
                    },
                    "type": {
                        "type": "string"
                    },
                    "language": {
                        "type": "string"
                    },
                    "raw_url": {
                        "type": "string"
                    },
                    "size": {
                        "type": "integer"
                    },
                    "truncated": {
                        "type": "boolean"
                    },
                    "content": {
                        "type": "string"
                    }
                }
            }
        },
        "public": {
            "type": "boolean"
        },
        "created_at": {
            "type": "string"
        },
        "updated_at": {
            "type": "string"
        },
        "description": {
            "type": "string",
            "nullable": true
        },
        "comments": {
            "type": "integer"
        },
        "user": {
            "type": "string",
            "nullable": true
        },
        "comments_url": {
            "type": "string"
        },
        "owner": {
            "$ref": "#/components/schemas/simple-user"
        },
        "truncated": {
            "type": "boolean"
        }
    }
}
```

### `#/components/examples/gist-fork-items`

```json
{
    "value": [
        {
            "url": "https://api.github.com/gists/aa5a315d61ae9438b18d",
            "forks_url": "https://api.github.com/gists/aa5a315d61ae9438b18d/forks",
            "commits_url": "https://api.github.com/gists/aa5a315d61ae9438b18d/commits",
            "id": "aa5a315d61ae9438b18d",
            "node_id": "MDQ6R2lzdGFhNWEzMTVkNjFhZTk0MzhiMThk",
            "git_pull_url": "https://gist.github.com/aa5a315d61ae9438b18d.git",
            "git_push_url": "https://gist.github.com/aa5a315d61ae9438b18d.git",
            "html_url": "https://gist.github.com/aa5a315d61ae9438b18d",
            "files": {
                "hello_world.rb": {
                    "filename": "hello_world.rb",
                    "type": "application/x-ruby",
                    "language": "Ruby",
                    "raw_url": "https://gist.githubusercontent.com/octocat/6cad326836d38bd3a7ae/raw/db9c55113504e46fa076e7df3a04ce592e2e86d8/hello_world.rb",
                    "size": 167
                }
            },
            "public": true,
            "created_at": "2010-04-14T02:15:15Z",
            "updated_at": "2011-06-20T11:34:15Z",
            "description": "Hello World Examples",
            "comments": 1,
            "user": null,
            "comments_url": "https://api.github.com/gists/aa5a315d61ae9438b18d/comments/",
            "owner": {
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