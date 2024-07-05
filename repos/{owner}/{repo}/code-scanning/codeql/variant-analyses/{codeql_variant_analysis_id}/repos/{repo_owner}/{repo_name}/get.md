# Get the analysis status of a repository in a CodeQL variant analysis

Gets the analysis status of a repository in a CodeQL variant analysis.

OAuth app tokens and personal access tokens (classic) need the `security_events` scope to use this endpoint with private or public repositories, or the `public_repo` scope to use this endpoint with only public repositories.

## Operation Object

```json
{
    "summary": "Get the analysis status of a repository in a CodeQL variant analysis",
    "description": "Gets the analysis status of a repository in a CodeQL variant analysis.\n\nOAuth app tokens and personal access tokens (classic) need the `security_events` scope to use this endpoint with private or public repositories, or the `public_repo` scope to use this endpoint with only public repositories.",
    "tags": [
        "code-scanning"
    ],
    "operationId": "code-scanning/get-variant-analysis-repo-task",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/code-scanning/code-scanning#get-the-analysis-status-of-a-repository-in-a-codeql-variant-analysis"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "name": "repo",
            "in": "path",
            "description": "The name of the controller repository.",
            "schema": {
                "type": "string"
            },
            "required": true
        },
        {
            "name": "codeql_variant_analysis_id",
            "in": "path",
            "description": "The ID of the variant analysis.",
            "schema": {
                "type": "integer"
            },
            "required": true
        },
        {
            "name": "repo_owner",
            "in": "path",
            "description": "The account owner of the variant analysis repository. The name is not case sensitive.",
            "schema": {
                "type": "string"
            },
            "required": true
        },
        {
            "name": "repo_name",
            "in": "path",
            "description": "The name of the variant analysis repository.",
            "schema": {
                "type": "string"
            },
            "required": true
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/code-scanning-variant-analysis-repo-task"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/code-scanning-variant-analysis-repo-task"
                        }
                    }
                }
            }
        },
        "404": {
            "$ref": "#/components/responses/not_found"
        },
        "503": {
            "$ref": "#/components/responses/service_unavailable"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "previews": [],
        "category": "code-scanning",
        "subcategory": "code-scanning"
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

### `#/components/schemas/code-scanning-variant-analysis-repo-task`

```json
{
    "type": "object",
    "properties": {
        "repository": {
            "$ref": "#/components/schemas/simple-repository"
        },
        "analysis_status": {
            "$ref": "#/components/schemas/code-scanning-variant-analysis-status"
        },
        "artifact_size_in_bytes": {
            "type": "integer",
            "description": "The size of the artifact. This is only available for successful analyses."
        },
        "result_count": {
            "type": "integer",
            "description": "The number of results in the case of a successful analysis. This is only available for successful analyses."
        },
        "failure_message": {
            "type": "string",
            "description": "The reason of the failure of this repo task. This is only available if the repository task has failed."
        },
        "database_commit_sha": {
            "type": "string",
            "description": "The SHA of the commit the CodeQL database was built against. This is only available for successful analyses."
        },
        "source_location_prefix": {
            "type": "string",
            "description": "The source location prefix to use. This is only available for successful analyses."
        },
        "artifact_url": {
            "type": "string",
            "description": "The URL of the artifact. This is only available for successful analyses."
        }
    },
    "required": [
        "repository",
        "analysis_status"
    ]
}
```

### `#/components/examples/code-scanning-variant-analysis-repo-task`

```json
{
    "summary": "Default response",
    "value": {
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
            "stargazers_url": "https://api.github.com/repos/octocat/Hello-World/stargazers",
            "statuses_url": "https://api.github.com/repos/octocat/Hello-World/statuses/{sha}",
            "subscribers_url": "https://api.github.com/repos/octocat/Hello-World/subscribers",
            "subscription_url": "https://api.github.com/repos/octocat/Hello-World/subscription",
            "tags_url": "https://api.github.com/repos/octocat/Hello-World/tags",
            "teams_url": "https://api.github.com/repos/octocat/Hello-World/teams",
            "trees_url": "https://api.github.com/repos/octocat/Hello-World/git/trees{/sha}",
            "hooks_url": "https://api.github.com/repos/octocat/Hello-World/hooks"
        },
        "analysis_status": "succeeded",
        "artifact_size_in_bytes": 12345,
        "result_count": 532,
        "database_commit_sha": "2d870c2a717a524627af38fa2da382188a096f90",
        "source_location_prefix": "/",
        "artifact_url": "https://example.com"
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

### `#/components/responses/service_unavailable`

```json
{
    "description": "Service unavailable",
    "content": {
        "application/json": {
            "schema": {
                "type": "object",
                "properties": {
                    "code": {
                        "type": "string"
                    },
                    "message": {
                        "type": "string"
                    },
                    "documentation_url": {
                        "type": "string"
                    }
                }
            }
        }
    }
}
```