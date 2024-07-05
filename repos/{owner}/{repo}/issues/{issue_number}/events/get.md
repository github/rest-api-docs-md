# List issue events

Lists all events for an issue.

## Operation Object

```json
{
    "summary": "List issue events",
    "description": "Lists all events for an issue.",
    "tags": [
        "issues"
    ],
    "operationId": "issues/list-events",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/issues/events#list-issue-events"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "$ref": "#/components/parameters/issue-number"
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
                            "$ref": "#/components/schemas/issue-event-for-issue"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/issue-event-for-issue-items"
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
        "410": {
            "$ref": "#/components/responses/gone"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "issues",
        "subcategory": "events"
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

### `#/components/parameters/issue-number`

```json
{
    "name": "issue_number",
    "description": "The number that identifies the issue.",
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

### `#/components/schemas/issue-event-for-issue`

```json
{
    "title": "Issue Event for Issue",
    "description": "Issue Event for Issue",
    "anyOf": [
        {
            "$ref": "#/components/schemas/labeled-issue-event"
        },
        {
            "$ref": "#/components/schemas/unlabeled-issue-event"
        },
        {
            "$ref": "#/components/schemas/assigned-issue-event"
        },
        {
            "$ref": "#/components/schemas/unassigned-issue-event"
        },
        {
            "$ref": "#/components/schemas/milestoned-issue-event"
        },
        {
            "$ref": "#/components/schemas/demilestoned-issue-event"
        },
        {
            "$ref": "#/components/schemas/renamed-issue-event"
        },
        {
            "$ref": "#/components/schemas/review-requested-issue-event"
        },
        {
            "$ref": "#/components/schemas/review-request-removed-issue-event"
        },
        {
            "$ref": "#/components/schemas/review-dismissed-issue-event"
        },
        {
            "$ref": "#/components/schemas/locked-issue-event"
        },
        {
            "$ref": "#/components/schemas/added-to-project-issue-event"
        },
        {
            "$ref": "#/components/schemas/moved-column-in-project-issue-event"
        },
        {
            "$ref": "#/components/schemas/removed-from-project-issue-event"
        },
        {
            "$ref": "#/components/schemas/converted-note-to-issue-issue-event"
        }
    ]
}
```

### `#/components/examples/issue-event-for-issue-items`

```json
{
    "value": [
        {
            "id": 1,
            "node_id": "MDEwOklzc3VlRXZlbnQx",
            "url": "https://api.github.com/repos/octocat/Hello-World/issues/events/1",
            "actor": {
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
            "event": "closed",
            "commit_id": "6dcb09b5b57875f334f61aebed695e2e4193db5e",
            "commit_url": "https://api.github.com/repos/octocat/Hello-World/commits/6dcb09b5b57875f334f61aebed695e2e4193db5e",
            "created_at": "2011-04-14T16:00:49Z",
            "performed_via_github_app": null,
            "label": {
                "name": "label",
                "color": "red"
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

### `#/components/responses/gone`

```json
{
    "description": "Gone",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/basic-error"
            }
        }
    }
}
```