# Get a discussion comment (Legacy)

`get /teams/{team_id}/discussions/{discussion_number}/comments/{comment_number}`

**Deprecation Notice:** This endpoint route is deprecated and will be removed from the Teams API. We recommend migrating your existing code to use the new [Get a discussion comment](https://docs.github.com/rest/teams/discussion-comments#get-a-discussion-comment) endpoint.

Get a specific comment on a team discussion.

OAuth app tokens and personal access tokens (classic) need the `read:discussion` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "Get a discussion comment (Legacy)",
    "description": "**Deprecation Notice:** This endpoint route is deprecated and will be removed from the Teams API. We recommend migrating your existing code to use the new [Get a discussion comment](https://docs.github.com/rest/teams/discussion-comments#get-a-discussion-comment) endpoint.\n\nGet a specific comment on a team discussion.\n\nOAuth app tokens and personal access tokens (classic) need the `read:discussion` scope to use this endpoint.",
    "tags": [
        "teams"
    ],
    "operationId": "teams/get-discussion-comment-legacy",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/teams/discussion-comments#get-a-discussion-comment-legacy"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/team-id"
        },
        {
            "$ref": "#/components/parameters/discussion-number"
        },
        {
            "$ref": "#/components/parameters/comment-number"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/team-discussion-comment"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/team-discussion-comment"
                        }
                    }
                }
            }
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "removalDate": "2021-02-01",
        "deprecationDate": "2020-01-21",
        "category": "teams",
        "subcategory": "discussion-comments"
    },
    "deprecated": true
}
```

## References

### `#/components/parameters/team-id`

```json
{
    "name": "team_id",
    "description": "The unique identifier of the team.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "integer"
    }
}
```

### `#/components/parameters/discussion-number`

```json
{
    "name": "discussion_number",
    "description": "The number that identifies the discussion.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "integer"
    }
}
```

### `#/components/parameters/comment-number`

```json
{
    "name": "comment_number",
    "description": "The number that identifies the comment.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "integer"
    }
}
```

### `#/components/schemas/team-discussion-comment`

```json
{
    "title": "Team Discussion Comment",
    "description": "A reply to a discussion within a team.",
    "type": "object",
    "properties": {
        "author": {
            "$ref": "#/components/schemas/nullable-simple-user"
        },
        "body": {
            "description": "The main text of the comment.",
            "example": "I agree with this suggestion.",
            "type": "string"
        },
        "body_html": {
            "type": "string",
            "example": "<p>Do you like apples?</p>"
        },
        "body_version": {
            "description": "The current version of the body content. If provided, this update operation will be rejected if the given version does not match the latest version on the server.",
            "example": "0307116bbf7ced493b8d8a346c650b71",
            "type": "string"
        },
        "created_at": {
            "type": "string",
            "format": "date-time",
            "example": "2018-01-15T23:53:58Z"
        },
        "last_edited_at": {
            "type": "string",
            "format": "date-time",
            "nullable": true
        },
        "discussion_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/organizations/1/team/2403582/discussions/1"
        },
        "html_url": {
            "type": "string",
            "format": "uri",
            "example": "https://github.com/orgs/github/teams/justice-league/discussions/1/comments/1"
        },
        "node_id": {
            "type": "string",
            "example": "MDIxOlRlYW1EaXNjdXNzaW9uQ29tbWVudDE="
        },
        "number": {
            "description": "The unique sequence number of a team discussion comment.",
            "example": 42,
            "type": "integer"
        },
        "updated_at": {
            "type": "string",
            "format": "date-time",
            "example": "2018-01-15T23:53:58Z"
        },
        "url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/organizations/1/team/2403582/discussions/1/comments/1"
        },
        "reactions": {
            "$ref": "#/components/schemas/reaction-rollup"
        }
    },
    "required": [
        "author",
        "body",
        "body_html",
        "body_version",
        "created_at",
        "last_edited_at",
        "discussion_url",
        "html_url",
        "node_id",
        "number",
        "updated_at",
        "url"
    ]
}
```

### `#/components/examples/team-discussion-comment`

```json
{
    "value": {
        "author": {
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
        "body": "Do you like apples?",
        "body_html": "<p>Do you like apples?</p>",
        "body_version": "5eb32b219cdc6a5a9b29ba5d6caa9c51",
        "created_at": "2018-01-15T23:53:58Z",
        "last_edited_at": null,
        "discussion_url": "https://api.github.com/teams/2403582/discussions/1",
        "html_url": "https://github.com/orgs/github/teams/justice-league/discussions/1/comments/1",
        "node_id": "MDIxOlRlYW1EaXNjdXNzaW9uQ29tbWVudDE=",
        "number": 1,
        "updated_at": "2018-01-15T23:53:58Z",
        "url": "https://api.github.com/teams/2403582/discussions/1/comments/1",
        "reactions": {
            "url": "https://api.github.com/teams/2403582/discussions/1/reactions",
            "total_count": 5,
            "+1": 3,
            "-1": 1,
            "laugh": 0,
            "confused": 0,
            "heart": 1,
            "hooray": 0,
            "eyes": 1,
            "rocket": 1
        }
    }
}
```