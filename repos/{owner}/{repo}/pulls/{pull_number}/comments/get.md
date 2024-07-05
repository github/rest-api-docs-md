# List review comments on a pull request

Lists all review comments for a specified pull request. By default, review comments
are in ascending order by ID.

This endpoint supports the following custom media types. For more information, see "[Media types](https://docs.github.com/rest/using-the-rest-api/getting-started-with-the-rest-api#media-types)."

- **`application/vnd.github-commitcomment.raw+json`**: Returns the raw markdown body. Response will include `body`. This is the default if you do not pass any specific media type.
- **`application/vnd.github-commitcomment.text+json`**: Returns a text only representation of the markdown body. Response will include `body_text`.
- **`application/vnd.github-commitcomment.html+json`**: Returns HTML rendered from the body's markdown. Response will include `body_html`.
- **`application/vnd.github-commitcomment.full+json`**: Returns raw, text, and HTML representations. Response will include `body`, `body_text`, and `body_html`.

## Operation Object

```json
{
    "summary": "List review comments on a pull request",
    "description": "Lists all review comments for a specified pull request. By default, review comments\nare in ascending order by ID.\n\nThis endpoint supports the following custom media types. For more information, see \"[Media types](https://docs.github.com/rest/using-the-rest-api/getting-started-with-the-rest-api#media-types).\"\n\n- **`application/vnd.github-commitcomment.raw+json`**: Returns the raw markdown body. Response will include `body`. This is the default if you do not pass any specific media type.\n- **`application/vnd.github-commitcomment.text+json`**: Returns a text only representation of the markdown body. Response will include `body_text`.\n- **`application/vnd.github-commitcomment.html+json`**: Returns HTML rendered from the body's markdown. Response will include `body_html`.\n- **`application/vnd.github-commitcomment.full+json`**: Returns raw, text, and HTML representations. Response will include `body`, `body_text`, and `body_html`.",
    "tags": [
        "pulls"
    ],
    "operationId": "pulls/list-review-comments",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/pulls/comments#list-review-comments-on-a-pull-request"
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
            "$ref": "#/components/parameters/sort"
        },
        {
            "name": "direction",
            "description": "The direction to sort results. Ignored without `sort` parameter.",
            "in": "query",
            "required": false,
            "schema": {
                "type": "string",
                "enum": [
                    "asc",
                    "desc"
                ]
            }
        },
        {
            "$ref": "#/components/parameters/since"
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
                            "$ref": "#/components/schemas/pull-request-review-comment"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/pull-request-review-comment-items"
                        }
                    }
                }
            },
            "headers": {
                "Link": {
                    "$ref": "#/components/headers/link"
                }
            }
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "pulls",
        "subcategory": "comments"
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

### `#/components/parameters/sort`

```json
{
    "name": "sort",
    "description": "The property to sort the results by.",
    "in": "query",
    "required": false,
    "schema": {
        "type": "string",
        "enum": [
            "created",
            "updated"
        ],
        "default": "created"
    }
}
```

### `#/components/parameters/since`

```json
{
    "name": "since",
    "description": "Only show results that were last updated after the given time. This is a timestamp in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format: `YYYY-MM-DDTHH:MM:SSZ`.",
    "in": "query",
    "required": false,
    "schema": {
        "type": "string",
        "format": "date-time"
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

### `#/components/schemas/pull-request-review-comment`

```json
{
    "title": "Pull Request Review Comment",
    "description": "Pull Request Review Comments are comments on a portion of the Pull Request's diff.",
    "type": "object",
    "properties": {
        "url": {
            "description": "URL for the pull request review comment",
            "example": "https://api.github.com/repos/octocat/Hello-World/pulls/comments/1",
            "type": "string"
        },
        "pull_request_review_id": {
            "description": "The ID of the pull request review to which the comment belongs.",
            "type": "integer",
            "format": "int64",
            "example": 42,
            "nullable": true
        },
        "id": {
            "description": "The ID of the pull request review comment.",
            "type": "integer",
            "format": "int64",
            "example": 1
        },
        "node_id": {
            "description": "The node ID of the pull request review comment.",
            "type": "string",
            "example": "MDI0OlB1bGxSZXF1ZXN0UmV2aWV3Q29tbWVudDEw"
        },
        "diff_hunk": {
            "description": "The diff of the line that the comment refers to.",
            "type": "string",
            "example": "@@ -16,33 +16,40 @@ public class Connection : IConnection..."
        },
        "path": {
            "description": "The relative path of the file to which the comment applies.",
            "example": "config/database.yaml",
            "type": "string"
        },
        "position": {
            "description": "The line index in the diff to which the comment applies. This field is deprecated; use `line` instead.",
            "example": 1,
            "type": "integer"
        },
        "original_position": {
            "description": "The index of the original line in the diff to which the comment applies. This field is deprecated; use `original_line` instead.",
            "example": 4,
            "type": "integer"
        },
        "commit_id": {
            "description": "The SHA of the commit to which the comment applies.",
            "example": "6dcb09b5b57875f334f61aebed695e2e4193db5e",
            "type": "string"
        },
        "original_commit_id": {
            "description": "The SHA of the original commit to which the comment applies.",
            "example": "9c48853fa3dc5c1c3d6f1f1cd1f2743e72652840",
            "type": "string"
        },
        "in_reply_to_id": {
            "description": "The comment ID to reply to.",
            "example": 8,
            "type": "integer"
        },
        "user": {
            "$ref": "#/components/schemas/simple-user"
        },
        "body": {
            "description": "The text of the comment.",
            "example": "We should probably include a check for null values here.",
            "type": "string"
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
            "description": "HTML URL for the pull request review comment.",
            "type": "string",
            "format": "uri",
            "example": "https://github.com/octocat/Hello-World/pull/1#discussion-diff-1"
        },
        "pull_request_url": {
            "description": "URL for the pull request that the review comment belongs to.",
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
                    "type": "object",
                    "properties": {
                        "href": {
                            "type": "string",
                            "format": "uri",
                            "example": "https://api.github.com/repos/octocat/Hello-World/pulls/comments/1"
                        }
                    },
                    "required": [
                        "href"
                    ]
                },
                "html": {
                    "type": "object",
                    "properties": {
                        "href": {
                            "type": "string",
                            "format": "uri",
                            "example": "https://github.com/octocat/Hello-World/pull/1#discussion-diff-1"
                        }
                    },
                    "required": [
                        "href"
                    ]
                },
                "pull_request": {
                    "type": "object",
                    "properties": {
                        "href": {
                            "type": "string",
                            "format": "uri",
                            "example": "https://api.github.com/repos/octocat/Hello-World/pulls/1"
                        }
                    },
                    "required": [
                        "href"
                    ]
                }
            },
            "required": [
                "self",
                "html",
                "pull_request"
            ]
        },
        "start_line": {
            "type": "integer",
            "description": "The first line of the range for a multi-line comment.",
            "example": 2,
            "nullable": true
        },
        "original_start_line": {
            "type": "integer",
            "description": "The first line of the range for a multi-line comment.",
            "example": 2,
            "nullable": true
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
            "description": "The line of the blob to which the comment applies. The last line of the range for a multi-line comment",
            "example": 2,
            "type": "integer"
        },
        "side": {
            "description": "The side of the diff to which the comment applies. The side of the last line of the range for a multi-line comment",
            "enum": [
                "LEFT",
                "RIGHT"
            ],
            "default": "RIGHT",
            "type": "string"
        },
        "subject_type": {
            "description": "The level at which the comment is targeted, can be a diff line or a file.",
            "type": "string",
            "enum": [
                "line",
                "file"
            ]
        },
        "reactions": {
            "$ref": "#/components/schemas/reaction-rollup"
        },
        "body_html": {
            "type": "string",
            "example": "\"<p>comment body</p>\""
        },
        "body_text": {
            "type": "string",
            "example": "\"comment body\""
        }
    },
    "required": [
        "url",
        "id",
        "node_id",
        "pull_request_review_id",
        "diff_hunk",
        "path",
        "commit_id",
        "original_commit_id",
        "user",
        "body",
        "created_at",
        "updated_at",
        "html_url",
        "pull_request_url",
        "author_association",
        "_links"
    ]
}
```

### `#/components/examples/pull-request-review-comment-items`

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
            },
            "start_line": 1,
            "original_start_line": 1,
            "start_side": "RIGHT",
            "line": 2,
            "original_line": 2,
            "side": "RIGHT"
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