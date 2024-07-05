# List check suites for a Git reference

Lists check suites for a commit `ref`. The `ref` can be a SHA, branch name, or a tag name.

**Note:** The endpoints to manage checks only look for pushes in the repository where the check suite or check run were created. Pushes to a branch in a forked repository are not detected and return an empty `pull_requests` array and a `null` value for `head_branch`.

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint on a private repository.

## Operation Object

```json
{
    "summary": "List check suites for a Git reference",
    "description": "Lists check suites for a commit `ref`. The `ref` can be a SHA, branch name, or a tag name.\n\n**Note:** The endpoints to manage checks only look for pushes in the repository where the check suite or check run were created. Pushes to a branch in a forked repository are not detected and return an empty `pull_requests` array and a `null` value for `head_branch`.\n\nOAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint on a private repository.",
    "tags": [
        "checks"
    ],
    "operationId": "checks/list-suites-for-ref",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/checks/suites#list-check-suites-for-a-git-reference"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "$ref": "#/components/parameters/commit-ref"
        },
        {
            "name": "app_id",
            "description": "Filters check suites by GitHub App `id`.",
            "in": "query",
            "required": false,
            "schema": {
                "type": "integer"
            },
            "example": 1
        },
        {
            "$ref": "#/components/parameters/check-name"
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
                        "type": "object",
                        "required": [
                            "total_count",
                            "check_suites"
                        ],
                        "properties": {
                            "total_count": {
                                "type": "integer"
                            },
                            "check_suites": {
                                "type": "array",
                                "items": {
                                    "$ref": "#/components/schemas/check-suite"
                                }
                            }
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/check-suite-paginated"
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
        "category": "checks",
        "subcategory": "suites"
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

### `#/components/parameters/commit-ref`

```json
{
    "name": "ref",
    "description": "The commit reference. Can be a commit SHA, branch name (`heads/BRANCH_NAME`), or tag name (`tags/TAG_NAME`). For more information, see \"[Git References](https://git-scm.com/book/en/v2/Git-Internals-Git-References)\" in the Git documentation.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "string"
    },
    "x-multi-segment": true
}
```

### `#/components/parameters/check-name`

```json
{
    "name": "check_name",
    "description": "Returns check runs with the specified `name`.",
    "in": "query",
    "required": false,
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

### `#/components/schemas/check-suite`

```json
{
    "title": "CheckSuite",
    "description": "A suite of checks performed on the code of a given code change",
    "type": "object",
    "properties": {
        "id": {
            "type": "integer",
            "example": 5
        },
        "node_id": {
            "type": "string",
            "example": "MDEwOkNoZWNrU3VpdGU1"
        },
        "head_branch": {
            "type": "string",
            "example": "master",
            "nullable": true
        },
        "head_sha": {
            "description": "The SHA of the head commit that is being checked.",
            "example": "009b8a3a9ccbb128af87f9b1c0f4c62e8a304f6d",
            "type": "string"
        },
        "status": {
            "type": "string",
            "description": "The phase of the lifecycle that the check suite is currently in. Statuses of waiting, requested, and pending are reserved for GitHub Actions check suites.",
            "example": "completed",
            "enum": [
                "queued",
                "in_progress",
                "completed",
                "waiting",
                "requested",
                "pending"
            ],
            "nullable": true
        },
        "conclusion": {
            "type": "string",
            "example": "neutral",
            "enum": [
                "success",
                "failure",
                "neutral",
                "cancelled",
                "skipped",
                "timed_out",
                "action_required",
                "startup_failure",
                "stale",
                null
            ],
            "nullable": true
        },
        "url": {
            "type": "string",
            "example": "https://api.github.com/repos/github/hello-world/check-suites/5",
            "nullable": true
        },
        "before": {
            "type": "string",
            "example": "146e867f55c26428e5f9fade55a9bbf5e95a7912",
            "nullable": true
        },
        "after": {
            "type": "string",
            "example": "d6fde92930d4715a2b49857d24b940956b26d2d3",
            "nullable": true
        },
        "pull_requests": {
            "type": "array",
            "items": {
                "$ref": "#/components/schemas/pull-request-minimal"
            },
            "nullable": true
        },
        "app": {
            "$ref": "#/components/schemas/nullable-integration"
        },
        "repository": {
            "$ref": "#/components/schemas/minimal-repository"
        },
        "created_at": {
            "type": "string",
            "format": "date-time",
            "nullable": true
        },
        "updated_at": {
            "type": "string",
            "format": "date-time",
            "nullable": true
        },
        "head_commit": {
            "$ref": "#/components/schemas/simple-commit"
        },
        "latest_check_runs_count": {
            "type": "integer"
        },
        "check_runs_url": {
            "type": "string"
        },
        "rerequestable": {
            "type": "boolean"
        },
        "runs_rerequestable": {
            "type": "boolean"
        }
    },
    "required": [
        "id",
        "node_id",
        "head_branch",
        "status",
        "conclusion",
        "head_sha",
        "url",
        "before",
        "after",
        "created_at",
        "updated_at",
        "app",
        "head_commit",
        "repository",
        "latest_check_runs_count",
        "check_runs_url",
        "pull_requests"
    ]
}
```

### `#/components/examples/check-suite-paginated`

```json
{
    "value": {
        "total_count": 1,
        "check_suites": [
            {
                "id": 5,
                "node_id": "MDEwOkNoZWNrU3VpdGU1",
                "head_branch": "master",
                "head_sha": "d6fde92930d4715a2b49857d24b940956b26d2d3",
                "status": "completed",
                "conclusion": "neutral",
                "url": "https://api.github.com/repos/github/hello-world/check-suites/5",
                "before": "146e867f55c26428e5f9fade55a9bbf5e95a7912",
                "after": "d6fde92930d4715a2b49857d24b940956b26d2d3",
                "pull_requests": [],
                "app": {
                    "id": 1,
                    "slug": "octoapp",
                    "node_id": "MDExOkludGVncmF0aW9uMQ==",
                    "owner": {
                        "login": "github",
                        "id": 1,
                        "node_id": "MDEyOk9yZ2FuaXphdGlvbjE=",
                        "url": "https://api.github.com/orgs/github",
                        "repos_url": "https://api.github.com/orgs/github/repos",
                        "events_url": "https://api.github.com/orgs/github/events",
                        "avatar_url": "https://github.com/images/error/octocat_happy.gif",
                        "gravatar_id": "",
                        "html_url": "https://github.com/octocat",
                        "followers_url": "https://api.github.com/users/octocat/followers",
                        "following_url": "https://api.github.com/users/octocat/following{/other_user}",
                        "gists_url": "https://api.github.com/users/octocat/gists{/gist_id}",
                        "starred_url": "https://api.github.com/users/octocat/starred{/owner}{/repo}",
                        "subscriptions_url": "https://api.github.com/users/octocat/subscriptions",
                        "organizations_url": "https://api.github.com/users/octocat/orgs",
                        "received_events_url": "https://api.github.com/users/octocat/received_events",
                        "type": "User",
                        "site_admin": true
                    },
                    "name": "Octocat App",
                    "description": "",
                    "external_url": "https://example.com",
                    "html_url": "https://github.com/apps/octoapp",
                    "created_at": "2017-07-08T16:18:44-04:00",
                    "updated_at": "2017-07-08T16:18:44-04:00",
                    "permissions": {
                        "metadata": "read",
                        "contents": "read",
                        "issues": "write",
                        "single_file": "write"
                    },
                    "events": [
                        "push",
                        "pull_request"
                    ]
                },
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
                    "temp_clone_token": "ABTLWHOULUVAXGTRYU7OC2876QJ2O",
                    "delete_branch_on_merge": true,
                    "subscribers_count": 42,
                    "network_count": 0
                },
                "created_at": "2011-01-26T19:01:12Z",
                "updated_at": "2011-01-26T19:14:43Z",
                "head_commit": {
                    "id": "7fd1a60b01f91b314f59955a4e4d4e80d8edf11d",
                    "tree_id": "7fd1a60b01f91b314f59955a4e4d4e80d8edf11d",
                    "message": "Merge pull request #6 from Spaceghost/patch-1\n\nNew line at end of file.",
                    "timestamp": "2016-10-10T00:00:00Z",
                    "author": {
                        "name": "The Octocat",
                        "email": "octocat@nowhere.com"
                    },
                    "committer": {
                        "name": "The Octocat",
                        "email": "octocat@nowhere.com"
                    }
                },
                "latest_check_runs_count": 1,
                "check_runs_url": "https://api.github.com/repos/octocat/Hello-World/check-suites/5/check-runs"
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