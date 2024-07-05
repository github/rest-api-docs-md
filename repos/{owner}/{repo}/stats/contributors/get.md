# Get all contributor commit activity

`get /repos/{owner}/{repo}/stats/contributors`


Returns the `total` number of commits authored by the contributor. In addition, the response includes a Weekly Hash (`weeks` array) with the following information:

*   `w` - Start of the week, given as a [Unix timestamp](https://en.wikipedia.org/wiki/Unix_time).
*   `a` - Number of additions
*   `d` - Number of deletions
*   `c` - Number of commits

**Note:** This endpoint will return `0` values for all addition and deletion counts in repositories with 10,000 or more commits.

## Operation Object

```json
{
    "summary": "Get all contributor commit activity",
    "description": "\nReturns the `total` number of commits authored by the contributor. In addition, the response includes a Weekly Hash (`weeks` array) with the following information:\n\n*   `w` - Start of the week, given as a [Unix timestamp](https://en.wikipedia.org/wiki/Unix_time).\n*   `a` - Number of additions\n*   `d` - Number of deletions\n*   `c` - Number of commits\n\n**Note:** This endpoint will return `0` values for all addition and deletion counts in repositories with 10,000 or more commits.",
    "tags": [
        "repos"
    ],
    "operationId": "repos/get-contributors-stats",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/metrics/statistics#get-all-contributor-commit-activity"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
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
                            "$ref": "#/components/schemas/contributor-activity"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/contributor-activity-items"
                        }
                    }
                }
            }
        },
        "202": {
            "$ref": "#/components/responses/accepted"
        },
        "204": {
            "$ref": "#/components/responses/no_content"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "metrics",
        "subcategory": "statistics"
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

### `#/components/schemas/contributor-activity`

```json
{
    "title": "Contributor Activity",
    "description": "Contributor Activity",
    "type": "object",
    "properties": {
        "author": {
            "$ref": "#/components/schemas/nullable-simple-user"
        },
        "total": {
            "type": "integer",
            "example": 135
        },
        "weeks": {
            "type": "array",
            "example": [
                {
                    "w": "1367712000",
                    "a": 6898,
                    "d": 77,
                    "c": 10
                }
            ],
            "items": {
                "type": "object",
                "properties": {
                    "w": {
                        "type": "integer"
                    },
                    "a": {
                        "type": "integer"
                    },
                    "d": {
                        "type": "integer"
                    },
                    "c": {
                        "type": "integer"
                    }
                }
            }
        }
    },
    "required": [
        "author",
        "total",
        "weeks"
    ]
}
```

### `#/components/examples/contributor-activity-items`

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
            "total": 135,
            "weeks": [
                {
                    "w": 1367712000,
                    "a": 6898,
                    "d": 77,
                    "c": 10
                }
            ]
        }
    ]
}
```

### `#/components/responses/accepted`

```json
{
    "description": "Accepted",
    "content": {
        "application/json": {
            "schema": {
                "type": "object"
            },
            "examples": {
                "default": {
                    "value": null
                }
            }
        }
    }
}
```

### `#/components/responses/no_content`

```json
{
    "description": "A header with no content is returned."
}
```