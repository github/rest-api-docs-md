# List issues assigned to the authenticated user

List issues assigned to the authenticated user across all visible repositories including owned repositories, member
repositories, and organization repositories. You can use the `filter` query parameter to fetch issues that are not
necessarily assigned to you.

**Note**: GitHub's REST API considers every pull request an issue, but not every issue is a pull request. For this
reason, "Issues" endpoints may return both issues and pull requests in the response. You can identify pull requests by
the `pull_request` key. Be aware that the `id` of a pull request returned from "Issues" endpoints will be an _issue id_. To find out the pull
request id, use the "[List pull requests](https://docs.github.com/rest/pulls/pulls#list-pull-requests)" endpoint.

This endpoint supports the following custom media types. For more information, see "[Media types](https://docs.github.com/rest/using-the-rest-api/getting-started-with-the-rest-api#media-types)."

- **`application/vnd.github.raw+json`**: Returns the raw markdown body. Response will include `body`. This is the default if you do not pass any specific media type.
- **`application/vnd.github.text+json`**: Returns a text only representation of the markdown body. Response will include `body_text`.
- **`application/vnd.github.html+json`**: Returns HTML rendered from the body's markdown. Response will include `body_html`.
- **`application/vnd.github.full+json`**: Returns raw, text, and HTML representations. Response will include `body`, `body_text`, and `body_html`.

## Operation Object

```json
{
    "summary": "List issues assigned to the authenticated user",
    "description": "List issues assigned to the authenticated user across all visible repositories including owned repositories, member\nrepositories, and organization repositories. You can use the `filter` query parameter to fetch issues that are not\nnecessarily assigned to you.\n\n**Note**: GitHub's REST API considers every pull request an issue, but not every issue is a pull request. For this\nreason, \"Issues\" endpoints may return both issues and pull requests in the response. You can identify pull requests by\nthe `pull_request` key. Be aware that the `id` of a pull request returned from \"Issues\" endpoints will be an _issue id_. To find out the pull\nrequest id, use the \"[List pull requests](https://docs.github.com/rest/pulls/pulls#list-pull-requests)\" endpoint.\n\nThis endpoint supports the following custom media types. For more information, see \"[Media types](https://docs.github.com/rest/using-the-rest-api/getting-started-with-the-rest-api#media-types).\"\n\n- **`application/vnd.github.raw+json`**: Returns the raw markdown body. Response will include `body`. This is the default if you do not pass any specific media type.\n- **`application/vnd.github.text+json`**: Returns a text only representation of the markdown body. Response will include `body_text`.\n- **`application/vnd.github.html+json`**: Returns HTML rendered from the body's markdown. Response will include `body_html`.\n- **`application/vnd.github.full+json`**: Returns raw, text, and HTML representations. Response will include `body`, `body_text`, and `body_html`.",
    "tags": [
        "issues"
    ],
    "operationId": "issues/list",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/issues/issues#list-issues-assigned-to-the-authenticated-user"
    },
    "parameters": [
        {
            "name": "filter",
            "description": "Indicates which sorts of issues to return. `assigned` means issues assigned to you. `created` means issues created by you. `mentioned` means issues mentioning you. `subscribed` means issues you're subscribed to updates for. `all` or `repos` means all issues you can see, regardless of participation or creation.",
            "in": "query",
            "required": false,
            "schema": {
                "type": "string",
                "enum": [
                    "assigned",
                    "created",
                    "mentioned",
                    "subscribed",
                    "repos",
                    "all"
                ],
                "default": "assigned"
            }
        },
        {
            "name": "state",
            "description": "Indicates the state of the issues to return.",
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
            "$ref": "#/components/parameters/labels"
        },
        {
            "name": "sort",
            "description": "What to sort results by.",
            "in": "query",
            "required": false,
            "schema": {
                "type": "string",
                "enum": [
                    "created",
                    "updated",
                    "comments"
                ],
                "default": "created"
            }
        },
        {
            "$ref": "#/components/parameters/direction"
        },
        {
            "$ref": "#/components/parameters/since"
        },
        {
            "name": "collab",
            "in": "query",
            "required": false,
            "schema": {
                "type": "boolean"
            }
        },
        {
            "name": "orgs",
            "in": "query",
            "required": false,
            "schema": {
                "type": "boolean"
            }
        },
        {
            "name": "owned",
            "in": "query",
            "required": false,
            "schema": {
                "type": "boolean"
            }
        },
        {
            "name": "pulls",
            "in": "query",
            "required": false,
            "schema": {
                "type": "boolean"
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
                            "$ref": "#/components/schemas/issue"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/issue-with-repo-items"
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
        },
        "304": {
            "$ref": "#/components/responses/not_modified"
        },
        "404": {
            "$ref": "#/components/responses/not_found"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": false,
        "category": "issues",
        "subcategory": "issues"
    }
}
```

## References

### `#/components/parameters/labels`

```json
{
    "name": "labels",
    "description": "A list of comma separated label names. Example: `bug,ui,@high`",
    "in": "query",
    "required": false,
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

### `#/components/parameters/since`

```json
{
    "name": "since",
    "description": "Only show results that were last updated after the given time. This is a timestamp in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format: `YYYY-MM-DDTHH:MM:SSZ`.",
    "in": "query",
    "required": false,
    "schema": {
        "type": "string",
        "format": "date-time"
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

### `#/components/schemas/issue`

```json
{
    "title": "Issue",
    "description": "Issues are a great way to keep track of tasks, enhancements, and bugs for your projects.",
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
            "description": "URL for the issue",
            "example": "https://api.github.com/repositories/42/issues/1",
            "type": "string",
            "format": "uri"
        },
        "repository_url": {
            "type": "string",
            "format": "uri"
        },
        "labels_url": {
            "type": "string"
        },
        "comments_url": {
            "type": "string",
            "format": "uri"
        },
        "events_url": {
            "type": "string",
            "format": "uri"
        },
        "html_url": {
            "type": "string",
            "format": "uri"
        },
        "number": {
            "description": "Number uniquely identifying the issue within its repository",
            "example": 42,
            "type": "integer"
        },
        "state": {
            "description": "State of the issue; either 'open' or 'closed'",
            "example": "open",
            "type": "string"
        },
        "state_reason": {
            "description": "The reason for the current state",
            "example": "not_planned",
            "type": "string",
            "nullable": true,
            "enum": [
                "completed",
                "reopened",
                "not_planned"
            ]
        },
        "title": {
            "description": "Title of the issue",
            "example": "Widget creation fails in Safari on OS X 10.8",
            "type": "string"
        },
        "body": {
            "description": "Contents of the issue",
            "example": "It looks like the new widget form is broken on Safari. When I try and create the widget, Safari crashes. This is reproducible on 10.8, but not 10.9. Maybe a browser bug?",
            "type": "string",
            "nullable": true
        },
        "user": {
            "$ref": "#/components/schemas/nullable-simple-user"
        },
        "labels": {
            "description": "Labels to associate with this issue; pass one or more label names to replace the set of labels on this issue; send an empty array to clear all labels from the issue; note that the labels are silently dropped for users without push access to the repository",
            "example": [
                "bug",
                "registration"
            ],
            "type": "array",
            "items": {
                "oneOf": [
                    {
                        "type": "string"
                    },
                    {
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
                                "type": "string",
                                "format": "uri"
                            },
                            "name": {
                                "type": "string"
                            },
                            "description": {
                                "type": "string",
                                "nullable": true
                            },
                            "color": {
                                "type": "string",
                                "nullable": true
                            },
                            "default": {
                                "type": "boolean"
                            }
                        }
                    }
                ]
            }
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
        "milestone": {
            "$ref": "#/components/schemas/nullable-milestone"
        },
        "locked": {
            "type": "boolean"
        },
        "active_lock_reason": {
            "type": "string",
            "nullable": true
        },
        "comments": {
            "type": "integer"
        },
        "pull_request": {
            "type": "object",
            "properties": {
                "merged_at": {
                    "type": "string",
                    "format": "date-time",
                    "nullable": true
                },
                "diff_url": {
                    "type": "string",
                    "format": "uri",
                    "nullable": true
                },
                "html_url": {
                    "type": "string",
                    "format": "uri",
                    "nullable": true
                },
                "patch_url": {
                    "type": "string",
                    "format": "uri",
                    "nullable": true
                },
                "url": {
                    "type": "string",
                    "format": "uri",
                    "nullable": true
                }
            },
            "required": [
                "diff_url",
                "html_url",
                "patch_url",
                "url"
            ]
        },
        "closed_at": {
            "type": "string",
            "format": "date-time",
            "nullable": true
        },
        "created_at": {
            "type": "string",
            "format": "date-time"
        },
        "updated_at": {
            "type": "string",
            "format": "date-time"
        },
        "draft": {
            "type": "boolean"
        },
        "closed_by": {
            "$ref": "#/components/schemas/nullable-simple-user"
        },
        "body_html": {
            "type": "string"
        },
        "body_text": {
            "type": "string"
        },
        "timeline_url": {
            "type": "string",
            "format": "uri"
        },
        "repository": {
            "$ref": "#/components/schemas/repository"
        },
        "performed_via_github_app": {
            "$ref": "#/components/schemas/nullable-integration"
        },
        "author_association": {
            "$ref": "#/components/schemas/author-association"
        },
        "reactions": {
            "$ref": "#/components/schemas/reaction-rollup"
        }
    },
    "required": [
        "assignee",
        "closed_at",
        "comments",
        "comments_url",
        "events_url",
        "html_url",
        "id",
        "node_id",
        "labels",
        "labels_url",
        "milestone",
        "number",
        "repository_url",
        "state",
        "locked",
        "title",
        "url",
        "user",
        "author_association",
        "created_at",
        "updated_at"
    ]
}
```

### `#/components/examples/issue-with-repo-items`

```json
{
    "value": [
        {
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
            "repository": {
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
            },
            "author_association": "COLLABORATOR"
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

### `#/components/responses/not_modified`

```json
{
    "description": "Not modified"
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