# Get the combined status for a specific reference

Users with pull access in a repository can access a combined view of commit statuses for a given ref. The ref can be a SHA, a branch name, or a tag name.


Additionally, a combined `state` is returned. The `state` is one of:

*   **failure** if any of the contexts report as `error` or `failure`
*   **pending** if there are no statuses or a context is `pending`
*   **success** if the latest status for all contexts is `success`

## Operation Object

```json
{
    "summary": "Get the combined status for a specific reference",
    "description": "Users with pull access in a repository can access a combined view of commit statuses for a given ref. The ref can be a SHA, a branch name, or a tag name.\n\n\nAdditionally, a combined `state` is returned. The `state` is one of:\n\n*   **failure** if any of the contexts report as `error` or `failure`\n*   **pending** if there are no statuses or a context is `pending`\n*   **success** if the latest status for all contexts is `success`",
    "tags": [
        "repos"
    ],
    "operationId": "repos/get-combined-status-for-ref",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/commits/statuses#get-the-combined-status-for-a-specific-reference"
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
                        "$ref": "#/components/schemas/combined-commit-status"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/combined-commit-status"
                        }
                    }
                }
            }
        },
        "404": {
            "$ref": "#/components/responses/not_found"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "commits",
        "subcategory": "statuses"
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

### `#/components/schemas/combined-commit-status`

```json
{
    "title": "Combined Commit Status",
    "description": "Combined Commit Status",
    "type": "object",
    "properties": {
        "state": {
            "type": "string"
        },
        "statuses": {
            "type": "array",
            "items": {
                "$ref": "#/components/schemas/simple-commit-status"
            }
        },
        "sha": {
            "type": "string"
        },
        "total_count": {
            "type": "integer"
        },
        "repository": {
            "$ref": "#/components/schemas/minimal-repository"
        },
        "commit_url": {
            "type": "string",
            "format": "uri"
        },
        "url": {
            "type": "string",
            "format": "uri"
        }
    },
    "required": [
        "state",
        "sha",
        "total_count",
        "statuses",
        "repository",
        "commit_url",
        "url"
    ]
}
```

### `#/components/examples/combined-commit-status`

```json
{
    "value": {
        "state": "success",
        "statuses": [
            {
                "url": "https://api.github.com/repos/octocat/Hello-World/statuses/6dcb09b5b57875f334f61aebed695e2e4193db5e",
                "avatar_url": "https://github.com/images/error/hubot_happy.gif",
                "id": 1,
                "node_id": "MDY6U3RhdHVzMQ==",
                "state": "success",
                "description": "Build has completed successfully",
                "target_url": "https://ci.example.com/1000/output",
                "context": "continuous-integration/jenkins",
                "created_at": "2012-07-20T01:19:13Z",
                "updated_at": "2012-07-20T01:19:13Z"
            },
            {
                "url": "https://api.github.com/repos/octocat/Hello-World/statuses/6dcb09b5b57875f334f61aebed695e2e4193db5e",
                "avatar_url": "https://github.com/images/error/other_user_happy.gif",
                "id": 2,
                "node_id": "MDY6U3RhdHVzMg==",
                "state": "success",
                "description": "Testing has completed successfully",
                "target_url": "https://ci.example.com/2000/output",
                "context": "security/brakeman",
                "created_at": "2012-08-20T01:19:13Z",
                "updated_at": "2012-08-20T01:19:13Z"
            }
        ],
        "sha": "6dcb09b5b57875f334f61aebed695e2e4193db5e",
        "total_count": 2,
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
            "hooks_url": "http://api.github.com/repos/octocat/Hello-World/hooks"
        },
        "commit_url": "https://api.github.com/repos/octocat/Hello-World/6dcb09b5b57875f334f61aebed695e2e4193db5e",
        "url": "https://api.github.com/repos/octocat/Hello-World/6dcb09b5b57875f334f61aebed695e2e4193db5e/status"
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