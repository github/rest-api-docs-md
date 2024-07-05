# Get an issue comment

You can use the REST API to get comments on issues and pull requests. Every pull request is an issue, but not every issue is a pull request.

This endpoint supports the following custom media types. For more information, see "[Media types](https://docs.github.com/rest/using-the-rest-api/getting-started-with-the-rest-api#media-types)."

- **`application/vnd.github.raw+json`**: Returns the raw markdown body. Response will include `body`. This is the default if you do not pass any specific media type.
- **`application/vnd.github.text+json`**: Returns a text only representation of the markdown body. Response will include `body_text`.
- **`application/vnd.github.html+json`**: Returns HTML rendered from the body's markdown. Response will include `body_html`.
- **`application/vnd.github.full+json`**: Returns raw, text, and HTML representations. Response will include `body`, `body_text`, and `body_html`.

## Operation Object

```json
{
    "summary": "Get an issue comment",
    "description": "You can use the REST API to get comments on issues and pull requests. Every pull request is an issue, but not every issue is a pull request.\n\nThis endpoint supports the following custom media types. For more information, see \"[Media types](https://docs.github.com/rest/using-the-rest-api/getting-started-with-the-rest-api#media-types).\"\n\n- **`application/vnd.github.raw+json`**: Returns the raw markdown body. Response will include `body`. This is the default if you do not pass any specific media type.\n- **`application/vnd.github.text+json`**: Returns a text only representation of the markdown body. Response will include `body_text`.\n- **`application/vnd.github.html+json`**: Returns HTML rendered from the body's markdown. Response will include `body_html`.\n- **`application/vnd.github.full+json`**: Returns raw, text, and HTML representations. Response will include `body`, `body_text`, and `body_html`.",
    "tags": [
        "issues"
    ],
    "operationId": "issues/get-comment",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/issues/comments#get-an-issue-comment"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
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
                        "$ref": "#/components/schemas/issue-comment"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/issue-comment"
                        }
                    }
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
        "category": "issues",
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

### `#/components/schemas/issue-comment`

```json
{
    "title": "Issue Comment",
    "description": "Comments provide a way for people to collaborate on an issue.",
    "type": "object",
    "properties": {
        "id": {
            "description": "Unique identifier of the issue comment",
            "example": 42,
            "type": "integer",
            "format": "int64"
        },
        "node_id": {
            "type": "string"
        },
        "url": {
            "description": "URL for the issue comment",
            "example": "https://api.github.com/repositories/42/issues/comments/1",
            "type": "string",
            "format": "uri"
        },
        "body": {
            "description": "Contents of the issue comment",
            "example": "What version of Safari were you using when you observed this bug?",
            "type": "string"
        },
        "body_text": {
            "type": "string"
        },
        "body_html": {
            "type": "string"
        },
        "html_url": {
            "type": "string",
            "format": "uri"
        },
        "user": {
            "$ref": "#/components/schemas/nullable-simple-user"
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
        "issue_url": {
            "type": "string",
            "format": "uri"
        },
        "author_association": {
            "$ref": "#/components/schemas/author-association"
        },
        "performed_via_github_app": {
            "$ref": "#/components/schemas/nullable-integration"
        },
        "reactions": {
            "$ref": "#/components/schemas/reaction-rollup"
        }
    },
    "required": [
        "id",
        "node_id",
        "html_url",
        "issue_url",
        "author_association",
        "user",
        "url",
        "created_at",
        "updated_at"
    ]
}
```

### `#/components/examples/issue-comment`

```json
{
    "value": {
        "id": 1,
        "node_id": "MDEyOklzc3VlQ29tbWVudDE=",
        "url": "https://api.github.com/repos/octocat/Hello-World/issues/comments/1",
        "html_url": "https://github.com/octocat/Hello-World/issues/1347#issuecomment-1",
        "body": "Me too",
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
        "created_at": "2011-04-14T16:00:49Z",
        "updated_at": "2011-04-14T16:00:49Z",
        "issue_url": "https://api.github.com/repos/octocat/Hello-World/issues/1347",
        "author_association": "COLLABORATOR"
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