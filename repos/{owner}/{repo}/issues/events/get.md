# List issue events for a repository

Lists events for a repository.

## Operation Object

```json
{
    "summary": "List issue events for a repository",
    "description": "Lists events for a repository.",
    "tags": [
        "issues"
    ],
    "operationId": "issues/list-events-for-repo",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/issues/events#list-issue-events-for-a-repository"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
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
                            "$ref": "#/components/schemas/issue-event"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/issue-event-items"
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
            "$ref": "#/components/responses/validation_failed"
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

### `#/components/schemas/issue-event`

```json
{
    "title": "Issue Event",
    "description": "Issue Event",
    "type": "object",
    "properties": {
        "id": {
            "type": "integer",
            "format": "int64",
            "example": 1
        },
        "node_id": {
            "type": "string",
            "example": "MDEwOklzc3VlRXZlbnQx"
        },
        "url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/repos/octocat/Hello-World/issues/events/1"
        },
        "actor": {
            "$ref": "#/components/schemas/nullable-simple-user"
        },
        "event": {
            "type": "string",
            "example": "closed"
        },
        "commit_id": {
            "type": "string",
            "example": "6dcb09b5b57875f334f61aebed695e2e4193db5e",
            "nullable": true
        },
        "commit_url": {
            "type": "string",
            "example": "https://api.github.com/repos/octocat/Hello-World/commits/6dcb09b5b57875f334f61aebed695e2e4193db5e",
            "nullable": true
        },
        "created_at": {
            "type": "string",
            "format": "date-time",
            "example": "2011-04-14T16:00:49Z"
        },
        "issue": {
            "$ref": "#/components/schemas/nullable-issue"
        },
        "label": {
            "$ref": "#/components/schemas/issue-event-label"
        },
        "assignee": {
            "$ref": "#/components/schemas/nullable-simple-user"
        },
        "assigner": {
            "$ref": "#/components/schemas/nullable-simple-user"
        },
        "review_requester": {
            "$ref": "#/components/schemas/nullable-simple-user"
        },
        "requested_reviewer": {
            "$ref": "#/components/schemas/nullable-simple-user"
        },
        "requested_team": {
            "$ref": "#/components/schemas/team"
        },
        "dismissed_review": {
            "$ref": "#/components/schemas/issue-event-dismissed-review"
        },
        "milestone": {
            "$ref": "#/components/schemas/issue-event-milestone"
        },
        "project_card": {
            "$ref": "#/components/schemas/issue-event-project-card"
        },
        "rename": {
            "$ref": "#/components/schemas/issue-event-rename"
        },
        "author_association": {
            "$ref": "#/components/schemas/author-association"
        },
        "lock_reason": {
            "type": "string",
            "nullable": true
        },
        "performed_via_github_app": {
            "$ref": "#/components/schemas/nullable-integration"
        }
    },
    "required": [
        "id",
        "node_id",
        "url",
        "actor",
        "event",
        "commit_id",
        "commit_url",
        "created_at"
    ]
}
```

### `#/components/examples/issue-event-items`

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
            "issue": {
                "id": 1,
                "node_id": "MDU6SXNzdWUx",
                "url": "https://api.github.com/repos/octocat/Hello-World/issues/1347",
                "repository_url": "https://api.github.com/repos/octocat/Hello-World",
                "labels_url": "https://api.github.com/repos/octocat/Hello-World/issues/1347/labels{/name}",
                "comments_url": "https://api.github.com/repos/octocat/Hello-World/issues/1347/comments",
                "events_url": "https://api.github.com/repos/octocat/Hello-World/issues/1347/events",
                "html_url": "https://github.com/octocat/Hello-World/issues/1347",
                "number": 1347,
                "state": "open",
                "title": "Found a bug",
                "body": "I'm having a problem with this.",
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
                "labels": [
                    {
                        "id": 208045946,
                        "node_id": "MDU6TGFiZWwyMDgwNDU5NDY=",
                        "url": "https://api.github.com/repos/octocat/Hello-World/labels/bug",
                        "name": "bug",
                        "description": "Something isn't working",
                        "color": "f29513",
                        "default": true
                    }
                ],
                "assignee": {
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
                "assignees": [
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
                "milestone": {
                    "url": "https://api.github.com/repos/octocat/Hello-World/milestones/1",
                    "html_url": "https://github.com/octocat/Hello-World/milestones/v1.0",
                    "labels_url": "https://api.github.com/repos/octocat/Hello-World/milestones/1/labels",
                    "id": 1002604,
                    "node_id": "MDk6TWlsZXN0b25lMTAwMjYwNA==",
                    "number": 1,
                    "state": "open",
                    "title": "v1.0",
                    "description": "Tracking milestone for version 1.0",
                    "creator": {
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
                    "open_issues": 4,
                    "closed_issues": 8,
                    "created_at": "2011-04-10T20:09:31Z",
                    "updated_at": "2014-03-03T18:58:10Z",
                    "closed_at": "2013-02-12T13:22:01Z",
                    "due_on": "2012-10-09T23:39:01Z"
                },
                "locked": true,
                "active_lock_reason": "too heated",
                "comments": 0,
                "pull_request": {
                    "url": "https://api.github.com/repos/octocat/Hello-World/pulls/1347",
                    "html_url": "https://github.com/octocat/Hello-World/pull/1347",
                    "diff_url": "https://github.com/octocat/Hello-World/pull/1347.diff",
                    "patch_url": "https://github.com/octocat/Hello-World/pull/1347.patch"
                },
                "closed_at": null,
                "created_at": "2011-04-22T13:33:48Z",
                "updated_at": "2011-04-22T13:33:48Z",
                "author_association": "COLLABORATOR",
                "state_reason": "completed"
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

### `#/components/responses/validation_failed`

```json
{
    "description": "Validation failed, or the endpoint has been spammed.",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/validation-error"
            }
        }
    }
}
```