# Get a gist comment

`get /gists/{gist_id}/comments/{comment_id}`

Gets a comment on a gist.

This endpoint supports the following custom media types. For more information, see "[Media types](https://docs.github.com/rest/using-the-rest-api/getting-started-with-the-rest-api#media-types)."

- **`application/vnd.github.raw+json`**: Returns the raw markdown. This is the default if you do not pass any specific media type.
- **`application/vnd.github.base64+json`**: Returns the base64-encoded contents. This can be useful if your gist contains any invalid UTF-8 sequences.

## Operation Object

```json
{
    "summary": "Get a gist comment",
    "description": "Gets a comment on a gist.\n\nThis endpoint supports the following custom media types. For more information, see \"[Media types](https://docs.github.com/rest/using-the-rest-api/getting-started-with-the-rest-api#media-types).\"\n\n- **`application/vnd.github.raw+json`**: Returns the raw markdown. This is the default if you do not pass any specific media type.\n- **`application/vnd.github.base64+json`**: Returns the base64-encoded contents. This can be useful if your gist contains any invalid UTF-8 sequences.",
    "tags": [
        "gists"
    ],
    "operationId": "gists/get-comment",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/gists/comments#get-a-gist-comment"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/gist-id"
        },
        {
            "$ref": "#/components/parameters/comment-id"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/gist-comment"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/gist-comment"
                        }
                    }
                }
            }
        },
        "304": {
            "$ref": "#/components/responses/not_modified"
        },
        "404": {
            "$ref": "#/components/responses/not_found"
        },
        "403": {
            "$ref": "#/components/responses/forbidden_gist"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": false,
        "category": "gists",
        "subcategory": "comments"
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

### `#/components/parameters/comment-id`

```json
{
    "name": "comment_id",
    "description": "The unique identifier of the comment.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "integer"
    }
}
```

### `#/components/schemas/gist-comment`

```json
{
    "title": "Gist Comment",
    "description": "A comment made to a gist.",
    "type": "object",
    "properties": {
        "id": {
            "type": "integer",
            "example": 1
        },
        "node_id": {
            "type": "string",
            "example": "MDExOkdpc3RDb21tZW50MQ=="
        },
        "url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/gists/a6db0bec360bb87e9418/comments/1"
        },
        "body": {
            "description": "The comment text.",
            "type": "string",
            "maxLength": 65535,
            "example": "Body of the attachment"
        },
        "user": {
            "$ref": "#/components/schemas/nullable-simple-user"
        },
        "created_at": {
            "type": "string",
            "format": "date-time",
            "example": "2011-04-18T23:23:56Z"
        },
        "updated_at": {
            "type": "string",
            "format": "date-time",
            "example": "2011-04-18T23:23:56Z"
        },
        "author_association": {
            "$ref": "#/components/schemas/author-association"
        }
    },
    "required": [
        "url",
        "id",
        "node_id",
        "user",
        "body",
        "author_association",
        "created_at",
        "updated_at"
    ]
}
```

### `#/components/examples/gist-comment`

```json
{
    "value": {
        "id": 1,
        "node_id": "MDExOkdpc3RDb21tZW50MQ==",
        "url": "https://api.github.com/gists/a6db0bec360bb87e9418/comments/1",
        "body": "Just commenting for the sake of commenting",
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
        "created_at": "2011-04-18T23:23:56Z",
        "updated_at": "2011-04-18T23:23:56Z",
        "author_association": "COLLABORATOR"
    }
}
```

### `#/components/responses/not_modified`

```json
{
    "description": "Not modified"
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

### `#/components/responses/forbidden_gist`

```json
{
    "description": "Forbidden Gist",
    "content": {
        "application/json": {
            "schema": {
                "type": "object",
                "properties": {
                    "block": {
                        "type": "object",
                        "properties": {
                            "reason": {
                                "type": "string"
                            },
                            "created_at": {
                                "type": "string"
                            },
                            "html_url": {
                                "type": "string",
                                "nullable": true
                            }
                        }
                    },
                    "message": {
                        "type": "string"
                    },
                    "documentation_url": {
                        "type": "string"
                    }
                }
            }
        }
    }
}
```