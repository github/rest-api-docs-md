# Get a review for a pull request

`get /repos/{owner}/{repo}/pulls/{pull_number}/reviews/{review_id}`

Retrieves a pull request review by its ID.

This endpoint supports the following custom media types. For more information, see "[Media types](https://docs.github.com/rest/using-the-rest-api/getting-started-with-the-rest-api#media-types)."

- **`application/vnd.github-commitcomment.raw+json`**: Returns the raw markdown body. Response will include `body`. This is the default if you do not pass any specific media type.
- **`application/vnd.github-commitcomment.text+json`**: Returns a text only representation of the markdown body. Response will include `body_text`.
- **`application/vnd.github-commitcomment.html+json`**: Returns HTML rendered from the body's markdown. Response will include `body_html`.
- **`application/vnd.github-commitcomment.full+json`**: Returns raw, text, and HTML representations. Response will include `body`, `body_text`, and `body_html`.

## Operation Object

```json
{
    "summary": "Get a review for a pull request",
    "description": "Retrieves a pull request review by its ID.\n\nThis endpoint supports the following custom media types. For more information, see \"[Media types](https://docs.github.com/rest/using-the-rest-api/getting-started-with-the-rest-api#media-types).\"\n\n- **`application/vnd.github-commitcomment.raw+json`**: Returns the raw markdown body. Response will include `body`. This is the default if you do not pass any specific media type.\n- **`application/vnd.github-commitcomment.text+json`**: Returns a text only representation of the markdown body. Response will include `body_text`.\n- **`application/vnd.github-commitcomment.html+json`**: Returns HTML rendered from the body's markdown. Response will include `body_html`.\n- **`application/vnd.github-commitcomment.full+json`**: Returns raw, text, and HTML representations. Response will include `body`, `body_text`, and `body_html`.",
    "tags": [
        "pulls"
    ],
    "operationId": "pulls/get-review",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/pulls/reviews#get-a-review-for-a-pull-request"
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
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/pull-request-review"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/pull-request-review-4"
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

### `#/components/schemas/pull-request-review`

```json
{
    "title": "Pull Request Review",
    "description": "Pull Request Reviews are reviews on pull requests.",
    "type": "object",
    "properties": {
        "id": {
            "description": "Unique identifier of the review",
            "example": 42,
            "type": "integer"
        },
        "node_id": {
            "type": "string",
            "example": "MDE3OlB1bGxSZXF1ZXN0UmV2aWV3ODA="
        },
        "user": {
            "$ref": "#/components/schemas/nullable-simple-user"
        },
        "body": {
            "description": "The text of the review.",
            "example": "This looks great.",
            "type": "string"
        },
        "state": {
            "type": "string",
            "example": "CHANGES_REQUESTED"
        },
        "html_url": {
            "type": "string",
            "format": "uri",
            "example": "https://github.com/octocat/Hello-World/pull/12#pullrequestreview-80"
        },
        "pull_request_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/repos/octocat/Hello-World/pulls/12"
        },
        "_links": {
            "type": "object",
            "properties": {
                "html": {
                    "type": "object",
                    "properties": {
                        "href": {
                            "type": "string"
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
                            "type": "string"
                        }
                    },
                    "required": [
                        "href"
                    ]
                }
            },
            "required": [
                "html",
                "pull_request"
            ]
        },
        "submitted_at": {
            "type": "string",
            "format": "date-time"
        },
        "commit_id": {
            "description": "A commit SHA for the review. If the commit object was garbage collected or forcibly deleted, then it no longer exists in Git and this value will be `null`.",
            "example": "54bb654c9e6025347f57900a4a5c2313a96b8035",
            "type": "string",
            "nullable": true
        },
        "body_html": {
            "type": "string"
        },
        "body_text": {
            "type": "string"
        },
        "author_association": {
            "$ref": "#/components/schemas/author-association"
        }
    },
    "required": [
        "id",
        "node_id",
        "user",
        "body",
        "state",
        "commit_id",
        "html_url",
        "pull_request_url",
        "_links",
        "author_association"
    ]
}
```

### `#/components/examples/pull-request-review-4`

```json
{
    "value": {
        "id": 80,
        "node_id": "MDE3OlB1bGxSZXF1ZXN0UmV2aWV3ODA=",
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
        "body": "Here is the body for the review.",
        "state": "APPROVED",
        "html_url": "https://github.com/octocat/Hello-World/pull/12#pullrequestreview-80",
        "pull_request_url": "https://api.github.com/repos/octocat/Hello-World/pulls/12",
        "_links": {
            "html": {
                "href": "https://github.com/octocat/Hello-World/pull/12#pullrequestreview-80"
            },
            "pull_request": {
                "href": "https://api.github.com/repos/octocat/Hello-World/pulls/12"
            }
        },
        "submitted_at": "2019-11-17T17:43:43Z",
        "commit_id": "ecdd80bb57125d7ba9641ffaa4d7d2c19d3f3091",
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