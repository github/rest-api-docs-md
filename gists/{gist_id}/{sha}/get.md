# Get a gist revision

`get /gists/{gist_id}/{sha}`

Gets a specified gist revision.

This endpoint supports the following custom media types. For more information, see "[Media types](https://docs.github.com/rest/using-the-rest-api/getting-started-with-the-rest-api#media-types)."

- **`application/vnd.github.raw+json`**: Returns the raw markdown. This is the default if you do not pass any specific media type.
- **`application/vnd.github.base64+json`**: Returns the base64-encoded contents. This can be useful if your gist contains any invalid UTF-8 sequences.

## Operation Object

```json
{
    "summary": "Get a gist revision",
    "description": "Gets a specified gist revision.\n\nThis endpoint supports the following custom media types. For more information, see \"[Media types](https://docs.github.com/rest/using-the-rest-api/getting-started-with-the-rest-api#media-types).\"\n\n- **`application/vnd.github.raw+json`**: Returns the raw markdown. This is the default if you do not pass any specific media type.\n- **`application/vnd.github.base64+json`**: Returns the base64-encoded contents. This can be useful if your gist contains any invalid UTF-8 sequences.",
    "tags": [
        "gists"
    ],
    "operationId": "gists/get-revision",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/gists/gists#get-a-gist-revision"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/gist-id"
        },
        {
            "name": "sha",
            "in": "path",
            "required": true,
            "schema": {
                "type": "string"
            }
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/gist-simple"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/gist"
                        }
                    }
                }
            }
        },
        "422": {
            "$ref": "#/components/responses/validation_failed"
        },
        "404": {
            "$ref": "#/components/responses/not_found"
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

### `#/components/examples/gist`

```json
{
    "value": {
        "url": "https://api.github.com/gists/2decf6c462d9b4418f2",
        "forks_url": "https://api.github.com/gists/2decf6c462d9b4418f2/forks",
        "commits_url": "https://api.github.com/gists/2decf6c462d9b4418f2/commits",
        "id": "2decf6c462d9b4418f2",
        "node_id": "G_kwDOBhHyLdZDliNDQxOGYy",
        "git_pull_url": "https://gist.github.com/2decf6c462d9b4418f2.git",
        "git_push_url": "https://gist.github.com/2decf6c462d9b4418f2.git",
        "html_url": "https://gist.github.com/2decf6c462d9b4418f2",
        "files": {
            "README.md": {
                "filename": "README.md",
                "type": "text/markdown",
                "language": "Markdown",
                "raw_url": "https://gist.githubusercontent.com/monalisa/2decf6c462d9b4418f2/raw/ac3e6daf176fafe73609fd000cd188e4472010fb/README.md",
                "size": 23,
                "truncated": false,
                "content": "Hello world from GitHub"
            }
        },
        "public": true,
        "created_at": "2022-09-20T12:11:58Z",
        "updated_at": "2022-09-21T10:28:06Z",
        "description": "An updated gist description.",
        "comments": 0,
        "user": null,
        "comments_url": "https://api.github.com/gists/2decf6c462d9b4418f2/comments",
        "owner": {
            "login": "monalisa",
            "id": 104456405,
            "node_id": "U_kgDOBhHyLQ",
            "avatar_url": "https://avatars.githubusercontent.com/u/104456405?v=4",
            "gravatar_id": "",
            "url": "https://api.github.com/users/monalisa",
            "html_url": "https://github.com/monalisa",
            "followers_url": "https://api.github.com/users/monalisa/followers",
            "following_url": "https://api.github.com/users/monalisa/following{/other_user}",
            "gists_url": "https://api.github.com/users/monalisa/gists{/gist_id}",
            "starred_url": "https://api.github.com/users/monalisa/starred{/owner}{/repo}",
            "subscriptions_url": "https://api.github.com/users/monalisa/subscriptions",
            "organizations_url": "https://api.github.com/users/monalisa/orgs",
            "repos_url": "https://api.github.com/users/monalisa/repos",
            "events_url": "https://api.github.com/users/monalisa/events{/privacy}",
            "received_events_url": "https://api.github.com/users/monalisa/received_events",
            "type": "User",
            "site_admin": true
        },
        "forks": [],
        "history": [
            {
                "user": {
                    "login": "monalisa",
                    "id": 104456405,
                    "node_id": "U_kgyLQ",
                    "avatar_url": "https://avatars.githubusercontent.com/u/104456405?v=4",
                    "gravatar_id": "",
                    "url": "https://api.github.com/users/monalisa",
                    "html_url": "https://github.com/monalisa",
                    "followers_url": "https://api.github.com/users/monalisa/followers",
                    "following_url": "https://api.github.com/users/monalisa/following{/other_user}",
                    "gists_url": "https://api.github.com/users/monalisa/gists{/gist_id}",
                    "starred_url": "https://api.github.com/users/monalisa/starred{/owner}{/repo}",
                    "subscriptions_url": "https://api.github.com/users/monalisa/subscriptions",
                    "organizations_url": "https://api.github.com/users/monalisa/orgs",
                    "repos_url": "https://api.github.com/users/monalisa/repos",
                    "events_url": "https://api.github.com/users/monalisa/events{/privacy}",
                    "received_events_url": "https://api.github.com/users/monalisa/received_events",
                    "type": "User",
                    "site_admin": true
                },
                "version": "468aac8caed5f0c3b859b8286968",
                "committed_at": "2022-09-21T10:28:06Z",
                "change_status": {
                    "total": 2,
                    "additions": 1,
                    "deletions": 1
                },
                "url": "https://api.github.com/gists/8481a81af6b7a2d418f2/468aac8caed5f0c3b859b8286968"
            }
        ],
        "truncated": false
    }
}
```

### `#/components/responses/validation_failed`

```json
{
    "description": "Validation failed, or the endpoint has been spammed.",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/validation-error"
            }
        }
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