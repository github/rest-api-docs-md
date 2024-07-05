# List pull requests

`get /repos/{owner}/{repo}/pulls`

Lists pull requests in a specified repository.

Draft pull requests are available in public repositories with GitHub
Free and GitHub Free for organizations, GitHub Pro, and legacy per-repository billing
plans, and in public and private repositories with GitHub Team and GitHub Enterprise
Cloud. For more information, see [GitHub's products](https://docs.github.com/github/getting-started-with-github/githubs-products)
in the GitHub Help documentation.

This endpoint supports the following custom media types. For more information, see "[Media types](https://docs.github.com/rest/using-the-rest-api/getting-started-with-the-rest-api#media-types)."

- **`application/vnd.github.raw+json`**: Returns the raw markdown body. Response will include `body`. This is the default if you do not pass any specific media type.
- **`application/vnd.github.text+json`**: Returns a text only representation of the markdown body. Response will include `body_text`.
- **`application/vnd.github.html+json`**: Returns HTML rendered from the body's markdown. Response will include `body_html`.
- **`application/vnd.github.full+json`**: Returns raw, text, and HTML representations. Response will include `body`, `body_text`, and `body_html`.

## Operation Object

```json
{
    "summary": "List pull requests",
    "description": "Lists pull requests in a specified repository.\n\nDraft pull requests are available in public repositories with GitHub\nFree and GitHub Free for organizations, GitHub Pro, and legacy per-repository billing\nplans, and in public and private repositories with GitHub Team and GitHub Enterprise\nCloud. For more information, see [GitHub's products](https://docs.github.com/github/getting-started-with-github/githubs-products)\nin the GitHub Help documentation.\n\nThis endpoint supports the following custom media types. For more information, see \"[Media types](https://docs.github.com/rest/using-the-rest-api/getting-started-with-the-rest-api#media-types).\"\n\n- **`application/vnd.github.raw+json`**: Returns the raw markdown body. Response will include `body`. This is the default if you do not pass any specific media type.\n- **`application/vnd.github.text+json`**: Returns a text only representation of the markdown body. Response will include `body_text`.\n- **`application/vnd.github.html+json`**: Returns HTML rendered from the body's markdown. Response will include `body_html`.\n- **`application/vnd.github.full+json`**: Returns raw, text, and HTML representations. Response will include `body`, `body_text`, and `body_html`.",
    "tags": [
        "pulls"
    ],
    "operationId": "pulls/list",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/pulls/pulls#list-pull-requests"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "name": "state",
            "description": "Either `open`, `closed`, or `all` to filter by state.",
            "in": "query",
            "required": false,
            "schema": {
                "type": "string",
                "enum": [
                    "open",
                    "closed",
                    "all"
                ],
                "default": "open"
            }
        },
        {
            "name": "head",
            "description": "Filter pulls by head user or head organization and branch name in the format of `user:ref-name` or `organization:ref-name`. For example: `github:new-script-format` or `octocat:test-branch`.",
            "in": "query",
            "required": false,
            "schema": {
                "type": "string"
            }
        },
        {
            "name": "base",
            "description": "Filter pulls by base branch name. Example: `gh-pages`.",
            "in": "query",
            "required": false,
            "schema": {
                "type": "string"
            }
        },
        {
            "name": "sort",
            "description": "What to sort results by. `popularity` will sort by the number of comments. `long-running` will sort by date created and will limit the results to pull requests that have been open for more than a month and have had activity within the past month.",
            "in": "query",
            "required": false,
            "schema": {
                "type": "string",
                "enum": [
                    "created",
                    "updated",
                    "popularity",
                    "long-running"
                ],
                "default": "created"
            }
        },
        {
            "name": "direction",
            "description": "The direction of the sort. Default: `desc` when sort is `created` or sort is not specified, otherwise `asc`.",
            "in": "query",
            "required": false,
            "schema": {
                "type": "string",
                "enum": [
                    "asc",
                    "desc"
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
                            "$ref": "#/components/schemas/pull-request-simple"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/pull-request-simple-items"
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
        "304": {
            "$ref": "#/components/responses/not_modified"
        },
        "422": {
            "$ref": "#/components/responses/validation_failed"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "pulls",
        "subcategory": "pulls"
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

### `#/components/schemas/pull-request-simple`

```json
{
    "title": "Pull Request Simple",
    "description": "Pull Request Simple",
    "type": "object",
    "properties": {
        "url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/repos/octocat/Hello-World/pulls/1347"
        },
        "id": {
            "type": "integer",
            "format": "int64",
            "example": 1
        },
        "node_id": {
            "type": "string",
            "example": "MDExOlB1bGxSZXF1ZXN0MQ=="
        },
        "html_url": {
            "type": "string",
            "format": "uri",
            "example": "https://github.com/octocat/Hello-World/pull/1347"
        },
        "diff_url": {
            "type": "string",
            "format": "uri",
            "example": "https://github.com/octocat/Hello-World/pull/1347.diff"
        },
        "patch_url": {
            "type": "string",
            "format": "uri",
            "example": "https://github.com/octocat/Hello-World/pull/1347.patch"
        },
        "issue_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/repos/octocat/Hello-World/issues/1347"
        },
        "commits_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/repos/octocat/Hello-World/pulls/1347/commits"
        },
        "review_comments_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/repos/octocat/Hello-World/pulls/1347/comments"
        },
        "review_comment_url": {
            "type": "string",
            "example": "https://api.github.com/repos/octocat/Hello-World/pulls/comments{/number}"
        },
        "comments_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/repos/octocat/Hello-World/issues/1347/comments"
        },
        "statuses_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/repos/octocat/Hello-World/statuses/6dcb09b5b57875f334f61aebed695e2e4193db5e"
        },
        "number": {
            "type": "integer",
            "example": 1347
        },
        "state": {
            "type": "string",
            "example": "open"
        },
        "locked": {
            "type": "boolean",
            "example": true
        },
        "title": {
            "type": "string",
            "example": "new-feature"
        },
        "user": {
            "$ref": "#/components/schemas/nullable-simple-user"
        },
        "body": {
            "type": "string",
            "example": "Please pull these awesome changes",
            "nullable": true
        },
        "labels": {
            "type": "array",
            "items": {
                "type": "object",
                "properties": {
                    "id": {
                        "type": "integer",
                        "format": "int64"
                    },
                    "node_id": {
                        "type": "string"
                    },
                    "url": {
                        "type": "string"
                    },
                    "name": {
                        "type": "string"
                    },
                    "description": {
                        "type": "string"
                    },
                    "color": {
                        "type": "string"
                    },
                    "default": {
                        "type": "boolean"
                    }
                },
                "required": [
                    "id",
                    "node_id",
                    "url",
                    "name",
                    "description",
                    "color",
                    "default"
                ]
            }
        },
        "milestone": {
            "$ref": "#/components/schemas/nullable-milestone"
        },
        "active_lock_reason": {
            "type": "string",
            "example": "too heated",
            "nullable": true
        },
        "created_at": {
            "type": "string",
            "format": "date-time",
            "example": "2011-01-26T19:01:12Z"
        },
        "updated_at": {
            "type": "string",
            "format": "date-time",
            "example": "2011-01-26T19:01:12Z"
        },
        "closed_at": {
            "type": "string",
            "format": "date-time",
            "example": "2011-01-26T19:01:12Z",
            "nullable": true
        },
        "merged_at": {
            "type": "string",
            "format": "date-time",
            "example": "2011-01-26T19:01:12Z",
            "nullable": true
        },
        "merge_commit_sha": {
            "type": "string",
            "example": "e5bd3914e2e596debea16f433f57875b5b90bcd6",
            "nullable": true
        },
        "assignee": {
            "$ref": "#/components/schemas/nullable-simple-user"
        },
        "assignees": {
            "type": "array",
            "items": {
                "$ref": "#/components/schemas/simple-user"
            },
            "nullable": true
        },
        "requested_reviewers": {
            "type": "array",
            "items": {
                "$ref": "#/components/schemas/simple-user"
            },
            "nullable": true
        },
        "requested_teams": {
            "type": "array",
            "items": {
                "$ref": "#/components/schemas/team"
            },
            "nullable": true
        },
        "head": {
            "type": "object",
            "properties": {
                "label": {
                    "type": "string"
                },
                "ref": {
                    "type": "string"
                },
                "repo": {
                    "$ref": "#/components/schemas/repository"
                },
                "sha": {
                    "type": "string"
                },
                "user": {
                    "$ref": "#/components/schemas/nullable-simple-user"
                }
            },
            "required": [
                "label",
                "ref",
                "repo",
                "sha",
                "user"
            ]
        },
        "base": {
            "type": "object",
            "properties": {
                "label": {
                    "type": "string"
                },
                "ref": {
                    "type": "string"
                },
                "repo": {
                    "$ref": "#/components/schemas/repository"
                },
                "sha": {
                    "type": "string"
                },
                "user": {
                    "$ref": "#/components/schemas/nullable-simple-user"
                }
            },
            "required": [
                "label",
                "ref",
                "repo",
                "sha",
                "user"
            ]
        },
        "_links": {
            "type": "object",
            "properties": {
                "comments": {
                    "$ref": "#/components/schemas/link"
                },
                "commits": {
                    "$ref": "#/components/schemas/link"
                },
                "statuses": {
                    "$ref": "#/components/schemas/link"
                },
                "html": {
                    "$ref": "#/components/schemas/link"
                },
                "issue": {
                    "$ref": "#/components/schemas/link"
                },
                "review_comments": {
                    "$ref": "#/components/schemas/link"
                },
                "review_comment": {
                    "$ref": "#/components/schemas/link"
                },
                "self": {
                    "$ref": "#/components/schemas/link"
                }
            },
            "required": [
                "comments",
                "commits",
                "statuses",
                "html",
                "issue",
                "review_comments",
                "review_comment",
                "self"
            ]
        },
        "author_association": {
            "$ref": "#/components/schemas/author-association"
        },
        "auto_merge": {
            "$ref": "#/components/schemas/auto-merge"
        },
        "draft": {
            "description": "Indicates whether or not the pull request is a draft.",
            "example": false,
            "type": "boolean"
        }
    },
    "required": [
        "_links",
        "assignee",
        "labels",
        "base",
        "body",
        "closed_at",
        "comments_url",
        "commits_url",
        "created_at",
        "diff_url",
        "head",
        "html_url",
        "id",
        "node_id",
        "issue_url",
        "merge_commit_sha",
        "merged_at",
        "milestone",
        "number",
        "patch_url",
        "review_comment_url",
        "review_comments_url",
        "statuses_url",
        "state",
        "locked",
        "title",
        "updated_at",
        "url",
        "user",
        "author_association",
        "auto_merge"
    ]
}
```

### `#/components/examples/pull-request-simple-items`

```json
{
    "value": [
        {
            "url": "https://api.github.com/repos/octocat/Hello-World/pulls/1347",
            "id": 1,
            "node_id": "MDExOlB1bGxSZXF1ZXN0MQ==",
            "html_url": "https://github.com/octocat/Hello-World/pull/1347",
            "diff_url": "https://github.com/octocat/Hello-World/pull/1347.diff",
            "patch_url": "https://github.com/octocat/Hello-World/pull/1347.patch",
            "issue_url": "https://api.github.com/repos/octocat/Hello-World/issues/1347",
            "commits_url": "https://api.github.com/repos/octocat/Hello-World/pulls/1347/commits",
            "review_comments_url": "https://api.github.com/repos/octocat/Hello-World/pulls/1347/comments",
            "review_comment_url": "https://api.github.com/repos/octocat/Hello-World/pulls/comments{/number}",
            "comments_url": "https://api.github.com/repos/octocat/Hello-World/issues/1347/comments",
            "statuses_url": "https://api.github.com/repos/octocat/Hello-World/statuses/6dcb09b5b57875f334f61aebed695e2e4193db5e",
            "number": 1347,
            "state": "open",
            "locked": true,
            "title": "Amazing new feature",
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
            "body": "Please pull these awesome changes in!",
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
            "active_lock_reason": "too heated",
            "created_at": "2011-01-26T19:01:12Z",
            "updated_at": "2011-01-26T19:01:12Z",
            "closed_at": "2011-01-26T19:01:12Z",
            "merged_at": "2011-01-26T19:01:12Z",
            "merge_commit_sha": "e5bd3914e2e596debea16f433f57875b5b90bcd6",
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
                },
                {
                    "login": "hubot",
                    "id": 1,
                    "node_id": "MDQ6VXNlcjE=",
                    "avatar_url": "https://github.com/images/error/hubot_happy.gif",
                    "gravatar_id": "",
                    "url": "https://api.github.com/users/hubot",
                    "html_url": "https://github.com/hubot",
                    "followers_url": "https://api.github.com/users/hubot/followers",
                    "following_url": "https://api.github.com/users/hubot/following{/other_user}",
                    "gists_url": "https://api.github.com/users/hubot/gists{/gist_id}",
                    "starred_url": "https://api.github.com/users/hubot/starred{/owner}{/repo}",
                    "subscriptions_url": "https://api.github.com/users/hubot/subscriptions",
                    "organizations_url": "https://api.github.com/users/hubot/orgs",
                    "repos_url": "https://api.github.com/users/hubot/repos",
                    "events_url": "https://api.github.com/users/hubot/events{/privacy}",
                    "received_events_url": "https://api.github.com/users/hubot/received_events",
                    "type": "User",
                    "site_admin": true
                }
            ],
            "requested_reviewers": [
                {
                    "login": "other_user",
                    "id": 1,
                    "node_id": "MDQ6VXNlcjE=",
                    "avatar_url": "https://github.com/images/error/other_user_happy.gif",
                    "gravatar_id": "",
                    "url": "https://api.github.com/users/other_user",
                    "html_url": "https://github.com/other_user",
                    "followers_url": "https://api.github.com/users/other_user/followers",
                    "following_url": "https://api.github.com/users/other_user/following{/other_user}",
                    "gists_url": "https://api.github.com/users/other_user/gists{/gist_id}",
                    "starred_url": "https://api.github.com/users/other_user/starred{/owner}{/repo}",
                    "subscriptions_url": "https://api.github.com/users/other_user/subscriptions",
                    "organizations_url": "https://api.github.com/users/other_user/orgs",
                    "repos_url": "https://api.github.com/users/other_user/repos",
                    "events_url": "https://api.github.com/users/other_user/events{/privacy}",
                    "received_events_url": "https://api.github.com/users/other_user/received_events",
                    "type": "User",
                    "site_admin": false
                }
            ],
            "requested_teams": [
                {
                    "id": 1,
                    "node_id": "MDQ6VGVhbTE=",
                    "url": "https://api.github.com/teams/1",
                    "html_url": "https://github.com/orgs/github/teams/justice-league",
                    "name": "Justice League",
                    "slug": "justice-league",
                    "description": "A great team.",
                    "privacy": "closed",
                    "permission": "admin",
                    "notification_setting": "notifications_enabled",
                    "members_url": "https://api.github.com/teams/1/members{/member}",
                    "repositories_url": "https://api.github.com/teams/1/repos",
                    "parent": null
                }
            ],
            "head": {
                "label": "octocat:new-topic",
                "ref": "new-topic",
                "sha": "6dcb09b5b57875f334f61aebed695e2e4193db5e",
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
                "repo": {
                    "id": 1296269,
                    "node_id": "MDEwOlJlcG9zaXRvcnkxMjk2MjY5",
                    "name": "Hello-World",
                    "full_name": "octocat/Hello-World",
                    "owner": {
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
                    "private": false,
                    "html_url": "https://github.com/octocat/Hello-World",
                    "description": "This your first repo!",
                    "fork": false,
                    "url": "https://api.github.com/repos/octocat/Hello-World",
                    "archive_url": "https://api.github.com/repos/octocat/Hello-World/{archive_format}{/ref}",
                    "assignees_url": "https://api.github.com/repos/octocat/Hello-World/assignees{/user}",
                    "blobs_url": "https://api.github.com/repos/octocat/Hello-World/git/blobs{/sha}",
                    "branches_url": "https://api.github.com/repos/octocat/Hello-World/branches{/branch}",
                    "collaborators_url": "https://api.github.com/repos/octocat/Hello-World/collaborators{/collaborator}",
                    "comments_url": "https://api.github.com/repos/octocat/Hello-World/comments{/number}",
                    "commits_url": "https://api.github.com/repos/octocat/Hello-World/commits{/sha}",
                    "compare_url": "https://api.github.com/repos/octocat/Hello-World/compare/{base}...{head}",
                    "contents_url": "https://api.github.com/repos/octocat/Hello-World/contents/{+path}",
                    "contributors_url": "https://api.github.com/repos/octocat/Hello-World/contributors",
                    "deployments_url": "https://api.github.com/repos/octocat/Hello-World/deployments",
                    "downloads_url": "https://api.github.com/repos/octocat/Hello-World/downloads",
                    "events_url": "https://api.github.com/repos/octocat/Hello-World/events",
                    "forks_url": "https://api.github.com/repos/octocat/Hello-World/forks",
                    "git_commits_url": "https://api.github.com/repos/octocat/Hello-World/git/commits{/sha}",
                    "git_refs_url": "https://api.github.com/repos/octocat/Hello-World/git/refs{/sha}",
                    "git_tags_url": "https://api.github.com/repos/octocat/Hello-World/git/tags{/sha}",
                    "git_url": "git:github.com/octocat/Hello-World.git",
                    "issue_comment_url": "https://api.github.com/repos/octocat/Hello-World/issues/comments{/number}",
                    "issue_events_url": "https://api.github.com/repos/octocat/Hello-World/issues/events{/number}",
                    "issues_url": "https://api.github.com/repos/octocat/Hello-World/issues{/number}",
                    "keys_url": "https://api.github.com/repos/octocat/Hello-World/keys{/key_id}",
                    "labels_url": "https://api.github.com/repos/octocat/Hello-World/labels{/name}",
                    "languages_url": "https://api.github.com/repos/octocat/Hello-World/languages",
                    "merges_url": "https://api.github.com/repos/octocat/Hello-World/merges",
                    "milestones_url": "https://api.github.com/repos/octocat/Hello-World/milestones{/number}",
                    "notifications_url": "https://api.github.com/repos/octocat/Hello-World/notifications{?since,all,participating}",
                    "pulls_url": "https://api.github.com/repos/octocat/Hello-World/pulls{/number}",
                    "releases_url": "https://api.github.com/repos/octocat/Hello-World/releases{/id}",
                    "ssh_url": "git@github.com:octocat/Hello-World.git",
                    "stargazers_url": "https://api.github.com/repos/octocat/Hello-World/stargazers",
                    "statuses_url": "https://api.github.com/repos/octocat/Hello-World/statuses/{sha}",
                    "subscribers_url": "https://api.github.com/repos/octocat/Hello-World/subscribers",
                    "subscription_url": "https://api.github.com/repos/octocat/Hello-World/subscription",
                    "tags_url": "https://api.github.com/repos/octocat/Hello-World/tags",
                    "teams_url": "https://api.github.com/repos/octocat/Hello-World/teams",
                    "trees_url": "https://api.github.com/repos/octocat/Hello-World/git/trees{/sha}",
                    "clone_url": "https://github.com/octocat/Hello-World.git",
                    "mirror_url": "git:git.example.com/octocat/Hello-World",
                    "hooks_url": "https://api.github.com/repos/octocat/Hello-World/hooks",
                    "svn_url": "https://svn.github.com/octocat/Hello-World",
                    "homepage": "https://github.com",
                    "language": null,
                    "forks_count": 9,
                    "stargazers_count": 80,
                    "watchers_count": 80,
                    "size": 108,
                    "default_branch": "master",
                    "open_issues_count": 0,
                    "is_template": true,
                    "topics": [
                        "octocat",
                        "atom",
                        "electron",
                        "api"
                    ],
                    "has_issues": true,
                    "has_projects": true,
                    "has_wiki": true,
                    "has_pages": false,
                    "has_downloads": true,
                    "archived": false,
                    "disabled": false,
                    "visibility": "public",
                    "pushed_at": "2011-01-26T19:06:43Z",
                    "created_at": "2011-01-26T19:01:12Z",
                    "updated_at": "2011-01-26T19:14:43Z",
                    "permissions": {
                        "admin": false,
                        "push": false,
                        "pull": true
                    },
                    "allow_rebase_merge": true,
                    "template_repository": null,
                    "temp_clone_token": "ABTLWHOULUVAXGTRYU7OC2876QJ2O",
                    "allow_squash_merge": true,
                    "allow_auto_merge": false,
                    "delete_branch_on_merge": true,
                    "allow_merge_commit": true,
                    "subscribers_count": 42,
                    "network_count": 0,
                    "license": {
                        "key": "mit",
                        "name": "MIT License",
                        "url": "https://api.github.com/licenses/mit",
                        "spdx_id": "MIT",
                        "node_id": "MDc6TGljZW5zZW1pdA==",
                        "html_url": "https://github.com/licenses/mit"
                    },
                    "forks": 1,
                    "open_issues": 1,
                    "watchers": 1
                }
            },
            "base": {
                "label": "octocat:master",
                "ref": "master",
                "sha": "6dcb09b5b57875f334f61aebed695e2e4193db5e",
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
                "repo": {
                    "id": 1296269,
                    "node_id": "MDEwOlJlcG9zaXRvcnkxMjk2MjY5",
                    "name": "Hello-World",
                    "full_name": "octocat/Hello-World",
                    "owner": {
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
                    "private": false,
                    "html_url": "https://github.com/octocat/Hello-World",
                    "description": "This your first repo!",
                    "fork": false,
                    "url": "https://api.github.com/repos/octocat/Hello-World",
                    "archive_url": "https://api.github.com/repos/octocat/Hello-World/{archive_format}{/ref}",
                    "assignees_url": "https://api.github.com/repos/octocat/Hello-World/assignees{/user}",
                    "blobs_url": "https://api.github.com/repos/octocat/Hello-World/git/blobs{/sha}",
                    "branches_url": "https://api.github.com/repos/octocat/Hello-World/branches{/branch}",
                    "collaborators_url": "https://api.github.com/repos/octocat/Hello-World/collaborators{/collaborator}",
                    "comments_url": "https://api.github.com/repos/octocat/Hello-World/comments{/number}",
                    "commits_url": "https://api.github.com/repos/octocat/Hello-World/commits{/sha}",
                    "compare_url": "https://api.github.com/repos/octocat/Hello-World/compare/{base}...{head}",
                    "contents_url": "https://api.github.com/repos/octocat/Hello-World/contents/{+path}",
                    "contributors_url": "https://api.github.com/repos/octocat/Hello-World/contributors",
                    "deployments_url": "https://api.github.com/repos/octocat/Hello-World/deployments",
                    "downloads_url": "https://api.github.com/repos/octocat/Hello-World/downloads",
                    "events_url": "https://api.github.com/repos/octocat/Hello-World/events",
                    "forks_url": "https://api.github.com/repos/octocat/Hello-World/forks",
                    "git_commits_url": "https://api.github.com/repos/octocat/Hello-World/git/commits{/sha}",
                    "git_refs_url": "https://api.github.com/repos/octocat/Hello-World/git/refs{/sha}",
                    "git_tags_url": "https://api.github.com/repos/octocat/Hello-World/git/tags{/sha}",
                    "git_url": "git:github.com/octocat/Hello-World.git",
                    "issue_comment_url": "https://api.github.com/repos/octocat/Hello-World/issues/comments{/number}",
                    "issue_events_url": "https://api.github.com/repos/octocat/Hello-World/issues/events{/number}",
                    "issues_url": "https://api.github.com/repos/octocat/Hello-World/issues{/number}",
                    "keys_url": "https://api.github.com/repos/octocat/Hello-World/keys{/key_id}",
                    "labels_url": "https://api.github.com/repos/octocat/Hello-World/labels{/name}",
                    "languages_url": "https://api.github.com/repos/octocat/Hello-World/languages",
                    "merges_url": "https://api.github.com/repos/octocat/Hello-World/merges",
                    "milestones_url": "https://api.github.com/repos/octocat/Hello-World/milestones{/number}",
                    "notifications_url": "https://api.github.com/repos/octocat/Hello-World/notifications{?since,all,participating}",
                    "pulls_url": "https://api.github.com/repos/octocat/Hello-World/pulls{/number}",
                    "releases_url": "https://api.github.com/repos/octocat/Hello-World/releases{/id}",
                    "ssh_url": "git@github.com:octocat/Hello-World.git",
                    "stargazers_url": "https://api.github.com/repos/octocat/Hello-World/stargazers",
                    "statuses_url": "https://api.github.com/repos/octocat/Hello-World/statuses/{sha}",
                    "subscribers_url": "https://api.github.com/repos/octocat/Hello-World/subscribers",
                    "subscription_url": "https://api.github.com/repos/octocat/Hello-World/subscription",
                    "tags_url": "https://api.github.com/repos/octocat/Hello-World/tags",
                    "teams_url": "https://api.github.com/repos/octocat/Hello-World/teams",
                    "trees_url": "https://api.github.com/repos/octocat/Hello-World/git/trees{/sha}",
                    "clone_url": "https://github.com/octocat/Hello-World.git",
                    "mirror_url": "git:git.example.com/octocat/Hello-World",
                    "hooks_url": "https://api.github.com/repos/octocat/Hello-World/hooks",
                    "svn_url": "https://svn.github.com/octocat/Hello-World",
                    "homepage": "https://github.com",
                    "language": null,
                    "forks_count": 9,
                    "stargazers_count": 80,
                    "watchers_count": 80,
                    "size": 108,
                    "default_branch": "master",
                    "open_issues_count": 0,
                    "is_template": true,
                    "topics": [
                        "octocat",
                        "atom",
                        "electron",
                        "api"
                    ],
                    "has_issues": true,
                    "has_projects": true,
                    "has_wiki": true,
                    "has_pages": false,
                    "has_downloads": true,
                    "archived": false,
                    "disabled": false,
                    "visibility": "public",
                    "pushed_at": "2011-01-26T19:06:43Z",
                    "created_at": "2011-01-26T19:01:12Z",
                    "updated_at": "2011-01-26T19:14:43Z",
                    "permissions": {
                        "admin": false,
                        "push": false,
                        "pull": true
                    },
                    "allow_rebase_merge": true,
                    "template_repository": null,
                    "temp_clone_token": "ABTLWHOULUVAXGTRYU7OC2876QJ2O",
                    "allow_squash_merge": true,
                    "allow_auto_merge": false,
                    "delete_branch_on_merge": true,
                    "allow_merge_commit": true,
                    "subscribers_count": 42,
                    "network_count": 0,
                    "license": {
                        "key": "mit",
                        "name": "MIT License",
                        "url": "https://api.github.com/licenses/mit",
                        "spdx_id": "MIT",
                        "node_id": "MDc6TGljZW5zZW1pdA==",
                        "html_url": "https://github.com/licenses/mit"
                    },
                    "forks": 1,
                    "open_issues": 1,
                    "watchers": 1
                }
            },
            "_links": {
                "self": {
                    "href": "https://api.github.com/repos/octocat/Hello-World/pulls/1347"
                },
                "html": {
                    "href": "https://github.com/octocat/Hello-World/pull/1347"
                },
                "issue": {
                    "href": "https://api.github.com/repos/octocat/Hello-World/issues/1347"
                },
                "comments": {
                    "href": "https://api.github.com/repos/octocat/Hello-World/issues/1347/comments"
                },
                "review_comments": {
                    "href": "https://api.github.com/repos/octocat/Hello-World/pulls/1347/comments"
                },
                "review_comment": {
                    "href": "https://api.github.com/repos/octocat/Hello-World/pulls/comments{/number}"
                },
                "commits": {
                    "href": "https://api.github.com/repos/octocat/Hello-World/pulls/1347/commits"
                },
                "statuses": {
                    "href": "https://api.github.com/repos/octocat/Hello-World/statuses/6dcb09b5b57875f334f61aebed695e2e4193db5e"
                }
            },
            "author_association": "OWNER",
            "auto_merge": null,
            "draft": false
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

### `#/components/responses/not_modified`

```json
{
    "description": "Not modified"
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