# Get an issue

The API returns a [`301 Moved Permanently` status](https://docs.github.com/rest/guides/best-practices-for-using-the-rest-api#follow-redirects) if the issue was
[transferred](https://docs.github.com/articles/transferring-an-issue-to-another-repository/) to another repository. If
the issue was transferred to or deleted from a repository where the authenticated user lacks read access, the API
returns a `404 Not Found` status. If the issue was deleted from a repository where the authenticated user has read
access, the API returns a `410 Gone` status. To receive webhook events for transferred and deleted issues, subscribe
to the [`issues`](https://docs.github.com/webhooks/event-payloads/#issues) webhook.

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
    "summary": "Get an issue",
    "description": "The API returns a [`301 Moved Permanently` status](https://docs.github.com/rest/guides/best-practices-for-using-the-rest-api#follow-redirects) if the issue was\n[transferred](https://docs.github.com/articles/transferring-an-issue-to-another-repository/) to another repository. If\nthe issue was transferred to or deleted from a repository where the authenticated user lacks read access, the API\nreturns a `404 Not Found` status. If the issue was deleted from a repository where the authenticated user has read\naccess, the API returns a `410 Gone` status. To receive webhook events for transferred and deleted issues, subscribe\nto the [`issues`](https://docs.github.com/webhooks/event-payloads/#issues) webhook.\n\n**Note**: GitHub's REST API considers every pull request an issue, but not every issue is a pull request. For this\nreason, \"Issues\" endpoints may return both issues and pull requests in the response. You can identify pull requests by\nthe `pull_request` key. Be aware that the `id` of a pull request returned from \"Issues\" endpoints will be an _issue id_. To find out the pull\nrequest id, use the \"[List pull requests](https://docs.github.com/rest/pulls/pulls#list-pull-requests)\" endpoint.\n\nThis endpoint supports the following custom media types. For more information, see \"[Media types](https://docs.github.com/rest/using-the-rest-api/getting-started-with-the-rest-api#media-types).\"\n\n- **`application/vnd.github.raw+json`**: Returns the raw markdown body. Response will include `body`. This is the default if you do not pass any specific media type.\n- **`application/vnd.github.text+json`**: Returns a text only representation of the markdown body. Response will include `body_text`.\n- **`application/vnd.github.html+json`**: Returns HTML rendered from the body's markdown. Response will include `body_html`.\n- **`application/vnd.github.full+json`**: Returns raw, text, and HTML representations. Response will include `body`, `body_text`, and `body_html`.",
    "tags": [
        "issues"
    ],
    "operationId": "issues/get",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/issues/issues#get-an-issue"
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
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/issue"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/issue"
                        }
                    }
                }
            }
        },
        "301": {
            "$ref": "#/components/responses/moved_permanently"
        },
        "404": {
            "$ref": "#/components/responses/not_found"
        },
        "410": {
            "$ref": "#/components/responses/gone"
        },
        "304": {
            "$ref": "#/components/responses/not_modified"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "issues",
        "subcategory": "issues"
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

### `#/components/examples/issue`

```json
{
    "value": {
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
        "closed_by": {
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
        "author_association": "COLLABORATOR",
        "state_reason": "completed"
    }
}
```

### `#/components/responses/moved_permanently`

```json
{
    "description": "Moved permanently",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/basic-error"
            }
        }
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

### `#/components/responses/not_modified`

```json
{
    "description": "Not modified"
}
```