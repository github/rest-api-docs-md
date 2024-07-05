# List discussion comments

`get /orgs/{org}/teams/{team_slug}/discussions/{discussion_number}/comments`

List all comments on a team discussion.

**Note:** You can also specify a team by `org_id` and `team_id` using the route `GET /organizations/{org_id}/team/{team_id}/discussions/{discussion_number}/comments`.

OAuth app tokens and personal access tokens (classic) need the `read:discussion` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "List discussion comments",
    "description": "List all comments on a team discussion.\n\n**Note:** You can also specify a team by `org_id` and `team_id` using the route `GET /organizations/{org_id}/team/{team_id}/discussions/{discussion_number}/comments`.\n\nOAuth app tokens and personal access tokens (classic) need the `read:discussion` scope to use this endpoint.",
    "tags": [
        "teams"
    ],
    "operationId": "teams/list-discussion-comments-in-org",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/teams/discussion-comments#list-discussion-comments"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/org"
        },
        {
            "$ref": "#/components/parameters/team-slug"
        },
        {
            "$ref": "#/components/parameters/discussion-number"
        },
        {
            "$ref": "#/components/parameters/direction"
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
                            "$ref": "#/components/schemas/team-discussion-comment"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/team-discussion-comment-items"
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
        "category": "teams",
        "subcategory": "discussion-comments"
    }
}
```

## References

### `#/components/parameters/org`

```json
{
    "name": "org",
    "description": "The organization name. The name is not case sensitive.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "string"
    }
}
```

### `#/components/parameters/team-slug`

```json
{
    "name": "team_slug",
    "description": "The slug of the team name.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "string"
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

### `#/components/parameters/direction`

```json
{
    "name": "direction",
    "description": "The direction to sort the results by.",
    "in": "query",
    "required": false,
    "schema": {
        "type": "string",
        "enum": [
            "asc",
            "desc"
        ],
        "default": "desc"
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

### `#/components/examples/team-discussion-comment-items`

```json
{
    "value": [
        {
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