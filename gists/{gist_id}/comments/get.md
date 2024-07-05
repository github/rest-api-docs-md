# List gist comments

Lists the comments on a gist.

This endpoint supports the following custom media types. For more information, see "[Media types](https://docs.github.com/rest/using-the-rest-api/getting-started-with-the-rest-api#media-types)."

- **`application/vnd.github.raw+json`**: Returns the raw markdown. This is the default if you do not pass any specific media type.
- **`application/vnd.github.base64+json`**: Returns the base64-encoded contents. This can be useful if your gist contains any invalid UTF-8 sequences.

## Operation Object

```json
{
    "summary": "List gist comments",
    "description": "Lists the comments on a gist.\n\nThis endpoint supports the following custom media types. For more information, see \"[Media types](https://docs.github.com/rest/using-the-rest-api/getting-started-with-the-rest-api#media-types).\"\n\n- **`application/vnd.github.raw+json`**: Returns the raw markdown. This is the default if you do not pass any specific media type.\n- **`application/vnd.github.base64+json`**: Returns the base64-encoded contents. This can be useful if your gist contains any invalid UTF-8 sequences.",
    "tags": [
        "gists"
    ],
    "operationId": "gists/list-comments",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/gists/comments#list-gist-comments"
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
                            "$ref": "#/components/schemas/gist-comment"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/gist-comment-items"
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
        "304": {
            "$ref": "#/components/responses/not_modified"
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

### `#/components/examples/gist-comment-items`

```json
{
    "value": [
        {
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