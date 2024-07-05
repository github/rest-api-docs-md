# List repository activities

Lists a detailed history of changes to a repository, such as pushes, merges, force pushes, and branch changes, and associates these changes with commits and users.

For more information about viewing repository activity,
see "[Viewing activity and data for your repository](https://docs.github.com/repositories/viewing-activity-and-data-for-your-repository)."

## Operation Object

```json
{
    "summary": "List repository activities",
    "description": "Lists a detailed history of changes to a repository, such as pushes, merges, force pushes, and branch changes, and associates these changes with commits and users.\n\nFor more information about viewing repository activity,\nsee \"[Viewing activity and data for your repository](https://docs.github.com/repositories/viewing-activity-and-data-for-your-repository).\"",
    "tags": [
        "repos"
    ],
    "operationId": "repos/list-activities",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/repos/repos#list-repository-activities"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "$ref": "#/components/parameters/direction"
        },
        {
            "$ref": "#/components/parameters/per-page"
        },
        {
            "$ref": "#/components/parameters/pagination-before"
        },
        {
            "$ref": "#/components/parameters/pagination-after"
        },
        {
            "name": "ref",
            "description": "The Git reference for the activities you want to list.\n\nThe `ref` for a branch can be formatted either as `refs/heads/BRANCH_NAME` or `BRANCH_NAME`, where `BRANCH_NAME` is the name of your branch.",
            "in": "query",
            "required": false,
            "schema": {
                "type": "string"
            }
        },
        {
            "name": "actor",
            "description": "The GitHub username to use to filter by the actor who performed the activity.",
            "in": "query",
            "required": false,
            "schema": {
                "type": "string"
            }
        },
        {
            "name": "time_period",
            "description": "The time period to filter by.\n\nFor example, `day` will filter for activity that occurred in the past 24 hours, and `week` will filter for activity that occurred in the past 7 days (168 hours).",
            "in": "query",
            "required": false,
            "schema": {
                "type": "string",
                "enum": [
                    "day",
                    "week",
                    "month",
                    "quarter",
                    "year"
                ]
            }
        },
        {
            "name": "activity_type",
            "description": "The activity type to filter by.\n\nFor example, you can choose to filter by \"force_push\", to see all force pushes to the repository.",
            "in": "query",
            "required": false,
            "schema": {
                "type": "string",
                "enum": [
                    "push",
                    "force_push",
                    "branch_creation",
                    "branch_deletion",
                    "pr_merge",
                    "merge_queue_merge"
                ]
            }
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
                            "$ref": "#/components/schemas/activity"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/activity-items"
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
        "422": {
            "$ref": "#/components/responses/validation_failed_simple"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "repos",
        "subcategory": "repos"
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

### `#/components/parameters/pagination-before`

```json
{
    "name": "before",
    "description": "A cursor, as given in the [Link header](https://docs.github.com/rest/guides/using-pagination-in-the-rest-api#using-link-headers). If specified, the query only searches for results before this cursor. For more information, see \"[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api).\"",
    "in": "query",
    "required": false,
    "schema": {
        "type": "string"
    }
}
```

### `#/components/parameters/pagination-after`

```json
{
    "name": "after",
    "description": "A cursor, as given in the [Link header](https://docs.github.com/rest/guides/using-pagination-in-the-rest-api#using-link-headers). If specified, the query only searches for results after this cursor. For more information, see \"[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api).\"",
    "in": "query",
    "required": false,
    "schema": {
        "type": "string"
    }
}
```

### `#/components/schemas/activity`

```json
{
    "title": "Activity",
    "description": "Activity",
    "type": "object",
    "properties": {
        "id": {
            "type": "integer",
            "example": 1296269
        },
        "node_id": {
            "type": "string",
            "example": "MDEwOlJlcG9zaXRvcnkxMjk2MjY5"
        },
        "before": {
            "type": "string",
            "example": "6dcb09b5b57875f334f61aebed695e2e4193db5e",
            "description": "The SHA of the commit before the activity."
        },
        "after": {
            "type": "string",
            "example": "827efc6d56897b048c772eb4087f854f46256132",
            "description": "The SHA of the commit after the activity."
        },
        "ref": {
            "type": "string",
            "example": "refs/heads/main",
            "description": "The full Git reference, formatted as `refs/heads/<branch name>`."
        },
        "timestamp": {
            "type": "string",
            "format": "date-time",
            "example": "2011-01-26T19:06:43Z",
            "description": "The time when the activity occurred."
        },
        "activity_type": {
            "type": "string",
            "example": "force_push",
            "enum": [
                "push",
                "force_push",
                "branch_deletion",
                "branch_creation",
                "pr_merge",
                "merge_queue_merge"
            ],
            "description": "The type of the activity that was performed."
        },
        "actor": {
            "$ref": "#/components/schemas/nullable-simple-user"
        }
    },
    "required": [
        "id",
        "node_id",
        "before",
        "after",
        "ref",
        "timestamp",
        "activity_type",
        "actor"
    ]
}
```

### `#/components/examples/activity-items`

```json
{
    "value": [
        {
            "id": 1296269,
            "node_id": "MDEwOlJlcG9zaXRvcnkxMjk2MjY5",
            "before": "6dcb09b5b57875f334f61aebed695e2e4193db5e",
            "after": "827efc6d56897b048c772eb4087f854f46256132",
            "ref": "refs/heads/main",
            "pushed_at": "2011-01-26T19:06:43Z",
            "push_type": "normal",
            "pusher": {
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

### `#/components/responses/validation_failed_simple`

```json
{
    "description": "Validation failed, or the endpoint has been spammed.",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/validation-error-simple"
            }
        }
    }
}
```