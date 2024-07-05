# List timeline events for an issue

`get /repos/{owner}/{repo}/issues/{issue_number}/timeline`

List all timeline events for an issue.

## Operation Object

```json
{
    "summary": "List timeline events for an issue",
    "description": "List all timeline events for an issue.",
    "tags": [
        "issues"
    ],
    "operationId": "issues/list-events-for-timeline",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/issues/timeline#list-timeline-events-for-an-issue"
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
                            "$ref": "#/components/schemas/timeline-issue-events"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/timeline-issue-events"
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
        "404": {
            "$ref": "#/components/responses/not_found"
        },
        "410": {
            "$ref": "#/components/responses/gone"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "issues",
        "subcategory": "timeline"
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

### `#/components/schemas/timeline-issue-events`

```json
{
    "title": "Timeline Event",
    "description": "Timeline Event",
    "type": "object",
    "anyOf": [
        {
            "$ref": "#/components/schemas/labeled-issue-event"
        },
        {
            "$ref": "#/components/schemas/unlabeled-issue-event"
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
        },
        {
            "$ref": "#/components/schemas/timeline-comment-event"
        },
        {
            "$ref": "#/components/schemas/timeline-cross-referenced-event"
        },
        {
            "$ref": "#/components/schemas/timeline-committed-event"
        },
        {
            "$ref": "#/components/schemas/timeline-reviewed-event"
        },
        {
            "$ref": "#/components/schemas/timeline-line-commented-event"
        },
        {
            "$ref": "#/components/schemas/timeline-commit-commented-event"
        },
        {
            "$ref": "#/components/schemas/timeline-assigned-issue-event"
        },
        {
            "$ref": "#/components/schemas/timeline-unassigned-issue-event"
        },
        {
            "$ref": "#/components/schemas/state-change-issue-event"
        }
    ]
}
```

### `#/components/examples/timeline-issue-events`

```json
{
    "value": [
        {
            "id": 6430295168,
            "node_id": "LOE_lADODwFebM5HwC0kzwAAAAF_RoSA",
            "url": "https://api.github.com/repos/github/roadmap/issues/events/6430295168",
            "actor": {
                "login": "github",
                "id": 9919,
                "node_id": "MDEyOk9yZ2FuaXphdGlvbjk5MTk=",
                "avatar_url": "https://avatars.githubusercontent.com/u/9919?v=4",
                "gravatar_id": "",
                "url": "https://api.github.com/users/github",
                "html_url": "https://github.com/github",
                "followers_url": "https://api.github.com/users/github/followers",
                "following_url": "https://api.github.com/users/github/following{/other_user}",
                "gists_url": "https://api.github.com/users/github/gists{/gist_id}",
                "starred_url": "https://api.github.com/users/github/starred{/owner}{/repo}",
                "subscriptions_url": "https://api.github.com/users/github/subscriptions",
                "organizations_url": "https://api.github.com/users/github/orgs",
                "repos_url": "https://api.github.com/users/github/repos",
                "events_url": "https://api.github.com/users/github/events{/privacy}",
                "received_events_url": "https://api.github.com/users/github/received_events",
                "type": "Organization",
                "site_admin": false
            },
            "event": "locked",
            "commit_id": null,
            "commit_url": null,
            "created_at": "2022-04-13T20:49:13Z",
            "lock_reason": null,
            "performed_via_github_app": null
        },
        {
            "id": 6430296748,
            "node_id": "LE_lADODwFebM5HwC0kzwAAAAF_Roqs",
            "url": "https://api.github.com/repos/github/roadmap/issues/events/6430296748",
            "actor": {
                "login": "github-product-roadmap",
                "id": 67656570,
                "node_id": "MDQ6VXNlcjY3NjU2NTcw",
                "avatar_url": "https://avatars.githubusercontent.com/u/67656570?v=4",
                "gravatar_id": "",
                "url": "https://api.github.com/users/github-product-roadmap",
                "html_url": "https://github.com/github-product-roadmap",
                "followers_url": "https://api.github.com/users/github-product-roadmap/followers",
                "following_url": "https://api.github.com/users/github-product-roadmap/following{/other_user}",
                "gists_url": "https://api.github.com/users/github-product-roadmap/gists{/gist_id}",
                "starred_url": "https://api.github.com/users/github-product-roadmap/starred{/owner}{/repo}",
                "subscriptions_url": "https://api.github.com/users/github-product-roadmap/subscriptions",
                "organizations_url": "https://api.github.com/users/github-product-roadmap/orgs",
                "repos_url": "https://api.github.com/users/github-product-roadmap/repos",
                "events_url": "https://api.github.com/users/github-product-roadmap/events{/privacy}",
                "received_events_url": "https://api.github.com/users/github-product-roadmap/received_events",
                "type": "User",
                "site_admin": false
            },
            "event": "labeled",
            "commit_id": null,
            "commit_url": null,
            "created_at": "2022-04-13T20:49:34Z",
            "label": {
                "name": "beta",
                "color": "99dd88"
            },
            "performed_via_github_app": null
        },
        {
            "id": 6635165802,
            "node_id": "RTE_lADODwFebM5HwC0kzwAAAAGLfJhq",
            "url": "https://api.github.com/repos/github/roadmap/issues/events/6635165802",
            "actor": {
                "login": "github-product-roadmap",
                "id": 67656570,
                "node_id": "MDQ6VXNlcjY3NjU2NTcw",
                "avatar_url": "https://avatars.githubusercontent.com/u/67656570?v=4",
                "gravatar_id": "",
                "url": "https://api.github.com/users/github-product-roadmap",
                "html_url": "https://github.com/github-product-roadmap",
                "followers_url": "https://api.github.com/users/github-product-roadmap/followers",
                "following_url": "https://api.github.com/users/github-product-roadmap/following{/other_user}",
                "gists_url": "https://api.github.com/users/github-product-roadmap/gists{/gist_id}",
                "starred_url": "https://api.github.com/users/github-product-roadmap/starred{/owner}{/repo}",
                "subscriptions_url": "https://api.github.com/users/github-product-roadmap/subscriptions",
                "organizations_url": "https://api.github.com/users/github-product-roadmap/orgs",
                "repos_url": "https://api.github.com/users/github-product-roadmap/repos",
                "events_url": "https://api.github.com/users/github-product-roadmap/events{/privacy}",
                "received_events_url": "https://api.github.com/users/github-product-roadmap/received_events",
                "type": "User",
                "site_admin": false
            },
            "event": "renamed",
            "commit_id": null,
            "commit_url": null,
            "created_at": "2022-05-18T19:29:01Z",
            "rename": {
                "from": "Secret scanning: dry-runs for enterprise-level custom patterns (cloud)",
                "to": "Secret scanning: dry-runs for enterprise-level custom patterns"
            },
            "performed_via_github_app": null
        },
        {
            "url": "https://api.github.com/repos/github/roadmap/issues/comments/1130876857",
            "html_url": "https://github.com/github/roadmap/issues/493#issuecomment-1130876857",
            "issue_url": "https://api.github.com/repos/github/roadmap/issues/493",
            "id": 1130876857,
            "node_id": "IC_kwDODwFebM5DZ8-5",
            "user": {
                "login": "octocat",
                "id": 94867353,
                "node_id": "U_kgDOBaePmQ",
                "avatar_url": "https://avatars.githubusercontent.com/u/94867353?v=4",
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
                "site_admin": true
            },
            "created_at": "2022-05-19T00:52:15Z",
            "updated_at": "2022-05-19T00:52:15Z",
            "author_association": "COLLABORATOR",
            "body": "\ud83d\udea2  Shipped to the cloud: https://github.blog/changelog/2022-05-12-secret-scanning-dry-runs-for-enterprise-level-custom-patterns/",
            "reactions": {
                "url": "https://api.github.com/repos/github/roadmap/issues/comments/1130876857/reactions",
                "total_count": 0,
                "+1": 0,
                "-1": 0,
                "laugh": 0,
                "hooray": 0,
                "confused": 0,
                "heart": 0,
                "rocket": 0,
                "eyes": 0
            },
            "performed_via_github_app": null,
            "event": "commented",
            "actor": {
                "login": "octocat",
                "id": 94867353,
                "node_id": "U_kgDOBaePmQ",
                "avatar_url": "https://avatars.githubusercontent.com/u/94867353?v=4",
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
                "site_admin": true
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