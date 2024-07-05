# List reactions for a team discussion comment

List the reactions to a [team discussion comment](https://docs.github.com/rest/teams/discussion-comments#get-a-discussion-comment).

**Note:** You can also specify a team by `org_id` and `team_id` using the route `GET /organizations/:org_id/team/:team_id/discussions/:discussion_number/comments/:comment_number/reactions`.

OAuth app tokens and personal access tokens (classic) need the `read:discussion` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "List reactions for a team discussion comment",
    "description": "List the reactions to a [team discussion comment](https://docs.github.com/rest/teams/discussion-comments#get-a-discussion-comment).\n\n**Note:** You can also specify a team by `org_id` and `team_id` using the route `GET /organizations/:org_id/team/:team_id/discussions/:discussion_number/comments/:comment_number/reactions`.\n\nOAuth app tokens and personal access tokens (classic) need the `read:discussion` scope to use this endpoint.",
    "tags": [
        "reactions"
    ],
    "operationId": "reactions/list-for-team-discussion-comment-in-org",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/reactions/reactions#list-reactions-for-a-team-discussion-comment"
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
            "$ref": "#/components/parameters/comment-number"
        },
        {
            "name": "content",
            "description": "Returns a single [reaction type](https://docs.github.com/rest/reactions/reactions#about-reactions). Omit this parameter to list all reactions to a team discussion comment.",
            "in": "query",
            "required": false,
            "schema": {
                "type": "string",
                "enum": [
                    "+1",
                    "-1",
                    "laugh",
                    "confused",
                    "heart",
                    "hooray",
                    "rocket",
                    "eyes"
                ]
            }
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
                            "$ref": "#/components/schemas/reaction"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/reaction-items"
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
        "category": "reactions",
        "subcategory": "reactions"
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

### `#/components/schemas/reaction`

```json
{
    "title": "Reaction",
    "description": "Reactions to conversations provide a way to help people express their feelings more simply and effectively.",
    "type": "object",
    "properties": {
        "id": {
            "type": "integer",
            "example": 1
        },
        "node_id": {
            "type": "string",
            "example": "MDg6UmVhY3Rpb24x"
        },
        "user": {
            "$ref": "#/components/schemas/nullable-simple-user"
        },
        "content": {
            "description": "The reaction to use",
            "example": "heart",
            "type": "string",
            "enum": [
                "+1",
                "-1",
                "laugh",
                "confused",
                "heart",
                "hooray",
                "rocket",
                "eyes"
            ]
        },
        "created_at": {
            "type": "string",
            "format": "date-time",
            "example": "2016-05-20T20:09:31Z"
        }
    },
    "required": [
        "id",
        "node_id",
        "user",
        "content",
        "created_at"
    ]
}
```

### `#/components/examples/reaction-items`

```json
{
    "value": [
        {
            "id": 1,
            "node_id": "MDg6UmVhY3Rpb24x",
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
            "content": "heart",
            "created_at": "2016-05-20T20:09:31Z"
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