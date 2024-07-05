# Get all requested reviewers for a pull request

Gets the users or teams whose review is requested for a pull request. Once a requested reviewer submits a review, they are no longer considered a requested reviewer. Their review will instead be returned by the [List reviews for a pull request](https://docs.github.com/rest/pulls/reviews#list-reviews-for-a-pull-request) operation.

## Operation Object

```json
{
    "summary": "Get all requested reviewers for a pull request",
    "description": "Gets the users or teams whose review is requested for a pull request. Once a requested reviewer submits a review, they are no longer considered a requested reviewer. Their review will instead be returned by the [List reviews for a pull request](https://docs.github.com/rest/pulls/reviews#list-reviews-for-a-pull-request) operation.",
    "tags": [
        "pulls"
    ],
    "operationId": "pulls/list-requested-reviewers",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/pulls/review-requests#get-all-requested-reviewers-for-a-pull-request"
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
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/pull-request-review-request"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/simple-pull-request-review-request"
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
        "subcategory": "review-requests"
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

### `#/components/schemas/pull-request-review-request`

```json
{
    "title": "Pull Request Review Request",
    "description": "Pull Request Review Request",
    "type": "object",
    "properties": {
        "users": {
            "type": "array",
            "items": {
                "$ref": "#/components/schemas/simple-user"
            }
        },
        "teams": {
            "type": "array",
            "items": {
                "$ref": "#/components/schemas/team"
            }
        }
    },
    "required": [
        "users",
        "teams"
    ]
}
```

### `#/components/examples/simple-pull-request-review-request`

```json
{
    "value": {
        "users": [
            {
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
            }
        ],
        "teams": [
            {
                "id": 1,
                "node_id": "MDQ6VGVhbTE=",
                "url": "https://api.github.com/teams/1",
                "html_url": "https://github.com/orgs/github/teams/justice-league",
                "name": "Justice League",
                "slug": "justice-league",
                "description": "A great team.",
                "privacy": "closed",
                "notification_setting": "notifications_enabled",
                "permission": "admin",
                "members_url": "https://api.github.com/teams/1/members{/member}",
                "repositories_url": "https://api.github.com/teams/1/repos",
                "parent": null
            }
        ]
    }
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