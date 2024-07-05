# List comments for a pull request review

Lists comments for a specific pull request review.

This endpoint supports the following custom media types. For more information, see "[Media types](https://docs.github.com/rest/using-the-rest-api/getting-started-with-the-rest-api#media-types)."

- **`application/vnd.github-commitcomment.raw+json`**: Returns the raw markdown body. Response will include `body`. This is the default if you do not pass any specific media type.
- **`application/vnd.github-commitcomment.text+json`**: Returns a text only representation of the markdown body. Response will include `body_text`.
- **`application/vnd.github-commitcomment.html+json`**: Returns HTML rendered from the body's markdown. Response will include `body_html`.
- **`application/vnd.github-commitcomment.full+json`**: Returns raw, text, and HTML representations. Response will include `body`, `body_text`, and `body_html`.

## Operation Object

```json
{
    "summary": "List comments for a pull request review",
    "description": "Lists comments for a specific pull request review.\n\nThis endpoint supports the following custom media types. For more information, see \"[Media types](https://docs.github.com/rest/using-the-rest-api/getting-started-with-the-rest-api#media-types).\"\n\n- **`application/vnd.github-commitcomment.raw+json`**: Returns the raw markdown body. Response will include `body`. This is the default if you do not pass any specific media type.\n- **`application/vnd.github-commitcomment.text+json`**: Returns a text only representation of the markdown body. Response will include `body_text`.\n- **`application/vnd.github-commitcomment.html+json`**: Returns HTML rendered from the body's markdown. Response will include `body_html`.\n- **`application/vnd.github-commitcomment.full+json`**: Returns raw, text, and HTML representations. Response will include `body`, `body_text`, and `body_html`.",
    "tags": [
        "pulls"
    ],
    "operationId": "pulls/list-comments-for-review",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/pulls/reviews#list-comments-for-a-pull-request-review"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "$ref": "#/components/parameters/pull-number"
        },
        {
            "$ref": "#/components/parameters/review-id"
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
                            "$ref": "#/components/schemas/review-comment"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/review-comment-items"
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
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "pulls",
        "subcategory": "reviews"
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

### `#/components/parameters/pull-number`

```json
{
    "name": "pull_number",
    "description": "The number that identifies the pull request.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "integer"
    }
}
```

### `#/components/parameters/review-id`

```json
{
    "name": "review_id",
    "description": "The unique identifier of the review.",
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

### `#/components/schemas/review-comment`

```json
{
    "title": "Legacy Review Comment",
    "description": "Legacy Review Comment",
    "type": "object",
    "properties": {
        "url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/repos/octocat/Hello-World/pulls/comments/1"
        },
        "pull_request_review_id": {
            "type": "integer",
            "format": "int64",
            "example": 42,
            "nullable": true
        },
        "id": {
            "type": "integer",
            "format": "int64",
            "example": 10
        },
        "node_id": {
            "type": "string",
            "example": "MDI0OlB1bGxSZXF1ZXN0UmV2aWV3Q29tbWVudDEw"
        },
        "diff_hunk": {
            "type": "string",
            "example": "@@ -16,33 +16,40 @@ public class Connection : IConnection..."
        },
        "path": {
            "type": "string",
            "example": "file1.txt"
        },
        "position": {
            "type": "integer",
            "example": 1,
            "nullable": true
        },
        "original_position": {
            "type": "integer",
            "example": 4
        },
        "commit_id": {
            "type": "string",
            "example": "6dcb09b5b57875f334f61aebed695e2e4193db5e"
        },
        "original_commit_id": {
            "type": "string",
            "example": "9c48853fa3dc5c1c3d6f1f1cd1f2743e72652840"
        },
        "in_reply_to_id": {
            "type": "integer",
            "example": 8
        },
        "user": {
            "$ref": "#/components/schemas/nullable-simple-user"
        },
        "body": {
            "type": "string",
            "example": "Great stuff"
        },
        "created_at": {
            "type": "string",
            "format": "date-time",
            "example": "2011-04-14T16:00:49Z"
        },
        "updated_at": {
            "type": "string",
            "format": "date-time",
            "example": "2011-04-14T16:00:49Z"
        },
        "html_url": {
            "type": "string",
            "format": "uri",
            "example": "https://github.com/octocat/Hello-World/pull/1#discussion-diff-1"
        },
        "pull_request_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/repos/octocat/Hello-World/pulls/1"
        },
        "author_association": {
            "$ref": "#/components/schemas/author-association"
        },
        "_links": {
            "type": "object",
            "properties": {
                "self": {
                    "$ref": "#/components/schemas/link"
                },
                "html": {
                    "$ref": "#/components/schemas/link"
                },
                "pull_request": {
                    "$ref": "#/components/schemas/link"
                }
            },
            "required": [
                "self",
                "html",
                "pull_request"
            ]
        },
        "body_text": {
            "type": "string"
        },
        "body_html": {
            "type": "string"
        },
        "reactions": {
            "$ref": "#/components/schemas/reaction-rollup"
        },
        "side": {
            "description": "The side of the first line of the range for a multi-line comment.",
            "enum": [
                "LEFT",
                "RIGHT"
            ],
            "default": "RIGHT",
            "type": "string"
        },
        "start_side": {
            "type": "string",
            "description": "The side of the first line of the range for a multi-line comment.",
            "enum": [
                "LEFT",
                "RIGHT"
            ],
            "default": "RIGHT",
            "nullable": true
        },
        "line": {
            "description": "The line of the blob to which the comment applies. The last line of the range for a multi-line comment",
            "example": 2,
            "type": "integer"
        },
        "original_line": {
            "description": "The original line of the blob to which the comment applies. The last line of the range for a multi-line comment",
            "example": 2,
            "type": "integer"
        },
        "start_line": {
            "description": "The first line of the range for a multi-line comment.",
            "example": 2,
            "type": "integer",
            "nullable": true
        },
        "original_start_line": {
            "description": "The original first line of the range for a multi-line comment.",
            "example": 2,
            "type": "integer",
            "nullable": true
        }
    },
    "required": [
        "id",
        "node_id",
        "url",
        "body",
        "diff_hunk",
        "path",
        "position",
        "original_position",
        "commit_id",
        "original_commit_id",
        "user",
        "pull_request_review_id",
        "html_url",
        "pull_request_url",
        "_links",
        "author_association",
        "created_at",
        "updated_at"
    ]
}
```

### `#/components/examples/review-comment-items`

```json
{
    "value": [
        {
            "url": "https://api.github.com/repos/octocat/Hello-World/pulls/comments/1",
            "pull_request_review_id": 42,
            "id": 10,
            "node_id": "MDI0OlB1bGxSZXF1ZXN0UmV2aWV3Q29tbWVudDEw",
            "diff_hunk": "@@ -16,33 +16,40 @@ public class Connection : IConnection...",
            "path": "file1.txt",
            "position": 1,
            "original_position": 4,
            "commit_id": "6dcb09b5b57875f334f61aebed695e2e4193db5e",
            "original_commit_id": "9c48853fa3dc5c1c3d6f1f1cd1f2743e72652840",
            "in_reply_to_id": 8,
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
            "body": "Great stuff!",
            "created_at": "2011-04-14T16:00:49Z",
            "updated_at": "2011-04-14T16:00:49Z",
            "html_url": "https://github.com/octocat/Hello-World/pull/1#discussion-diff-1",
            "pull_request_url": "https://api.github.com/repos/octocat/Hello-World/pulls/1",
            "author_association": "NONE",
            "_links": {
                "self": {
                    "href": "https://api.github.com/repos/octocat/Hello-World/pulls/comments/1"
                },
                "html": {
                    "href": "https://github.com/octocat/Hello-World/pull/1#discussion-diff-1"
                },
                "pull_request": {
                    "href": "https://api.github.com/repos/octocat/Hello-World/pulls/1"
                }
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