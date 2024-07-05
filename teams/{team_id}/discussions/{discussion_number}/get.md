# Get a discussion (Legacy)

`get /teams/{team_id}/discussions/{discussion_number}`

**Deprecation Notice:** This endpoint route is deprecated and will be removed from the Teams API. We recommend migrating your existing code to use the new [Get a discussion](https://docs.github.com/rest/teams/discussions#get-a-discussion) endpoint.

Get a specific discussion on a team's page.

OAuth app tokens and personal access tokens (classic) need the `read:discussion` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "Get a discussion (Legacy)",
    "description": "**Deprecation Notice:** This endpoint route is deprecated and will be removed from the Teams API. We recommend migrating your existing code to use the new [Get a discussion](https://docs.github.com/rest/teams/discussions#get-a-discussion) endpoint.\n\nGet a specific discussion on a team's page.\n\nOAuth app tokens and personal access tokens (classic) need the `read:discussion` scope to use this endpoint.",
    "tags": [
        "teams"
    ],
    "operationId": "teams/get-discussion-legacy",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/teams/discussions#get-a-discussion-legacy"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/team-id"
        },
        {
            "$ref": "#/components/parameters/discussion-number"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/team-discussion"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/team-discussion"
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
        "subcategory": "discussions"
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

### `#/components/schemas/team-discussion`

```json
{
    "title": "Team Discussion",
    "description": "A team discussion is a persistent record of a free-form conversation within a team.",
    "type": "object",
    "properties": {
        "author": {
            "$ref": "#/components/schemas/nullable-simple-user"
        },
        "body": {
            "description": "The main text of the discussion.",
            "example": "Please suggest improvements to our workflow in comments.",
            "type": "string"
        },
        "body_html": {
            "type": "string",
            "example": "<p>Hi! This is an area for us to collaborate as a team</p>"
        },
        "body_version": {
            "description": "The current version of the body content. If provided, this update operation will be rejected if the given version does not match the latest version on the server.",
            "example": "0307116bbf7ced493b8d8a346c650b71",
            "type": "string"
        },
        "comments_count": {
            "type": "integer",
            "example": 0
        },
        "comments_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/organizations/1/team/2343027/discussions/1/comments"
        },
        "created_at": {
            "type": "string",
            "format": "date-time",
            "example": "2018-01-25T18:56:31Z"
        },
        "last_edited_at": {
            "type": "string",
            "format": "date-time",
            "nullable": true
        },
        "html_url": {
            "type": "string",
            "format": "uri",
            "example": "https://github.com/orgs/github/teams/justice-league/discussions/1"
        },
        "node_id": {
            "type": "string",
            "example": "MDE0OlRlYW1EaXNjdXNzaW9uMQ=="
        },
        "number": {
            "description": "The unique sequence number of a team discussion.",
            "example": 42,
            "type": "integer"
        },
        "pinned": {
            "description": "Whether or not this discussion should be pinned for easy retrieval.",
            "example": true,
            "type": "boolean"
        },
        "private": {
            "description": "Whether or not this discussion should be restricted to team members and organization owners.",
            "example": true,
            "type": "boolean"
        },
        "team_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/organizations/1/team/2343027"
        },
        "title": {
            "description": "The title of the discussion.",
            "example": "How can we improve our workflow?",
            "type": "string"
        },
        "updated_at": {
            "type": "string",
            "format": "date-time",
            "example": "2018-01-25T18:56:31Z"
        },
        "url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/organizations/1/team/2343027/discussions/1"
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
        "comments_count",
        "comments_url",
        "created_at",
        "last_edited_at",
        "html_url",
        "pinned",
        "private",
        "node_id",
        "number",
        "team_url",
        "title",
        "updated_at",
        "url"
    ]
}
```

### `#/components/examples/team-discussion`

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
        "body": "Hi! This is an area for us to collaborate as a team.",
        "body_html": "<p>Hi! This is an area for us to collaborate as a team</p>",
        "body_version": "0d495416a700fb06133c612575d92bfb",
        "comments_count": 0,
        "comments_url": "https://api.github.com/teams/2343027/discussions/1/comments",
        "created_at": "2018-01-25T18:56:31Z",
        "last_edited_at": null,
        "html_url": "https://github.com/orgs/github/teams/justice-league/discussions/1",
        "node_id": "MDE0OlRlYW1EaXNjdXNzaW9uMQ==",
        "number": 1,
        "pinned": false,
        "private": false,
        "team_url": "https://api.github.com/teams/2343027",
        "title": "Our first team post",
        "updated_at": "2018-01-25T18:56:31Z",
        "url": "https://api.github.com/teams/2343027/discussions/1",
        "reactions": {
            "url": "https://api.github.com/teams/2343027/discussions/1/reactions",
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