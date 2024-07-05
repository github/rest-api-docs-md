# List locations for a secret scanning alert

Lists all locations for a given secret scanning alert for an eligible repository.

The authenticated user must be an administrator for the repository or for the organization that owns the repository to use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `repo` or `security_events` scope to use this endpoint. If this endpoint is only used with public repositories, the token can use the `public_repo` scope instead.

## Operation Object

```json
{
    "summary": "List locations for a secret scanning alert",
    "description": "Lists all locations for a given secret scanning alert for an eligible repository.\n\nThe authenticated user must be an administrator for the repository or for the organization that owns the repository to use this endpoint.\n\nOAuth app tokens and personal access tokens (classic) need the `repo` or `security_events` scope to use this endpoint. If this endpoint is only used with public repositories, the token can use the `public_repo` scope instead.",
    "tags": [
        "secret-scanning"
    ],
    "operationId": "secret-scanning/list-locations-for-alert",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/secret-scanning/secret-scanning#list-locations-for-a-secret-scanning-alert"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "$ref": "#/components/parameters/alert-number"
        },
        {
            "$ref": "#/components/parameters/page"
        },
        {
            "$ref": "#/components/parameters/per-page"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "type": "array",
                        "description": "List of locations where the secret was detected",
                        "items": {
                            "$ref": "#/components/schemas/secret-scanning-location"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/secret-scanning-location-list"
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
            "description": "Repository is public, or secret scanning is disabled for the repository, or the resource is not found"
        },
        "503": {
            "$ref": "#/components/responses/service_unavailable"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "secret-scanning",
        "subcategory": "secret-scanning"
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

### `#/components/parameters/alert-number`

```json
{
    "name": "alert_number",
    "in": "path",
    "description": "The number that identifies an alert. You can find this at the end of the URL for a code scanning alert within GitHub, and in the `number` field in the response from the `GET /repos/{owner}/{repo}/code-scanning/alerts` operation.",
    "required": true,
    "schema": {
        "$ref": "#/components/schemas/alert-number"
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

### `#/components/schemas/secret-scanning-location`

```json
{
    "type": "object",
    "properties": {
        "type": {
            "type": "string",
            "enum": [
                "commit",
                "wiki_commit",
                "issue_title",
                "issue_body",
                "issue_comment",
                "discussion_title",
                "discussion_body",
                "discussion_comment",
                "pull_request_title",
                "pull_request_body",
                "pull_request_comment",
                "pull_request_review",
                "pull_request_review_comment"
            ],
            "description": "The location type. Because secrets may be found in different types of resources (ie. code, comments, issues, pull requests, discussions), this field identifies the type of resource where the secret was found.",
            "example": "commit"
        },
        "details": {
            "oneOf": [
                {
                    "$ref": "#/components/schemas/secret-scanning-location-commit"
                },
                {
                    "$ref": "#/components/schemas/secret-scanning-location-wiki-commit"
                },
                {
                    "$ref": "#/components/schemas/secret-scanning-location-issue-title"
                },
                {
                    "$ref": "#/components/schemas/secret-scanning-location-issue-body"
                },
                {
                    "$ref": "#/components/schemas/secret-scanning-location-issue-comment"
                },
                {
                    "$ref": "#/components/schemas/secret-scanning-location-discussion-title"
                },
                {
                    "$ref": "#/components/schemas/secret-scanning-location-discussion-body"
                },
                {
                    "$ref": "#/components/schemas/secret-scanning-location-discussion-comment"
                },
                {
                    "$ref": "#/components/schemas/secret-scanning-location-pull-request-title"
                },
                {
                    "$ref": "#/components/schemas/secret-scanning-location-pull-request-body"
                },
                {
                    "$ref": "#/components/schemas/secret-scanning-location-pull-request-comment"
                },
                {
                    "$ref": "#/components/schemas/secret-scanning-location-pull-request-review"
                },
                {
                    "$ref": "#/components/schemas/secret-scanning-location-pull-request-review-comment"
                }
            ]
        }
    }
}
```

### `#/components/examples/secret-scanning-location-list`

```json
{
    "value": [
        {
            "type": "commit",
            "details": {
                "path": "/example/secrets.txt",
                "start_line": 1,
                "end_line": 1,
                "start_column": 1,
                "end_column": 64,
                "blob_sha": "af5626b4a114abcb82d63db7c8082c3c4756e51b",
                "blob_url": "https://api.github.com/repos/octocat/hello-world/git/blobs/af5626b4a114abcb82d63db7c8082c3c4756e51b",
                "commit_sha": "f14d7debf9775f957cf4f1e8176da0786431f72b",
                "commit_url": "https://api.github.com/repos/octocat/hello-world/git/commits/f14d7debf9775f957cf4f1e8176da0786431f72b"
            }
        },
        {
            "type": "wiki_commit",
            "details": {
                "path": "/example/Home.md",
                "start_line": 1,
                "end_line": 1,
                "start_column": 1,
                "end_column": 64,
                "blob_sha": "af5626b4a114abcb82d63db7c8082c3c4756e51b",
                "page_url": "https://github.com/octocat/Hello-World/wiki/Home/302c0b7e200761c9dd9b57e57db540ee0b4293a5",
                "commit_sha": "302c0b7e200761c9dd9b57e57db540ee0b4293a5",
                "commit_url": "https://github.com/octocat/Hello-World/wiki/_compare/302c0b7e200761c9dd9b57e57db540ee0b4293a5"
            }
        },
        {
            "type": "issue_title",
            "details": {
                "issue_title_url": "https://api.github.com/repos/octocat/Hello-World/issues/1347"
            }
        },
        {
            "type": "issue_body",
            "details": {
                "issue_body_url": "https://api.github.com/repos/octocat/Hello-World/issues/1347"
            }
        },
        {
            "type": "issue_comment",
            "details": {
                "issue_comment_url": "https://api.github.com/repos/octocat/Hello-World/issues/comments/1081119451"
            }
        },
        {
            "type": "discussion_title",
            "details": {
                "discussion_title_url": "https://github.com/community/community/discussions/39082"
            }
        },
        {
            "type": "discussion_body",
            "details": {
                "discussion_body_url": "https://github.com/community/community/discussions/39082#discussion-4566270"
            }
        },
        {
            "type": "discussion_comment",
            "details": {
                "discussion_comment_url": "https://github.com/community/community/discussions/39082#discussioncomment-4158232"
            }
        },
        {
            "type": "pull_request_title",
            "details": {
                "pull_request_title_url": "https://api.github.com/repos/octocat/Hello-World/pull/2846"
            }
        },
        {
            "type": "pull_request_body",
            "details": {
                "pull_request_body_url": "https://api.github.com/repos/octocat/Hello-World/pulls/2846"
            }
        },
        {
            "type": "pull_request_comment",
            "details": {
                "pull_request_comment_url": "https://api.github.com/repos/octocat/Hello-World/issues/comments/1825855898"
            }
        },
        {
            "type": "pull_request_review",
            "details": {
                "pull_request_review_url": "https://api.github.com/repos/octocat/Hello-World/pulls/2846/reviews/80"
            }
        },
        {
            "type": "pull_request_review_comment",
            "details": {
                "pull_request_review_comment_url": "https://api.github.com/repos/octocat/Hello-World/pulls/comments/12"
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

### `#/components/responses/service_unavailable`

```json
{
    "description": "Service unavailable",
    "content": {
        "application/json": {
            "schema": {
                "type": "object",
                "properties": {
                    "code": {
                        "type": "string"
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