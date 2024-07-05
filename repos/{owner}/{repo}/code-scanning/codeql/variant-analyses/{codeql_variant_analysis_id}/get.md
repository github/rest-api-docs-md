# Get the summary of a CodeQL variant analysis

`get /repos/{owner}/{repo}/code-scanning/codeql/variant-analyses/{codeql_variant_analysis_id}`

Gets the summary of a CodeQL variant analysis.

OAuth app tokens and personal access tokens (classic) need the `security_events` scope to use this endpoint with private or public repositories, or the `public_repo` scope to use this endpoint with only public repositories.

## Operation Object

```json
{
    "summary": "Get the summary of a CodeQL variant analysis",
    "description": "Gets the summary of a CodeQL variant analysis.\n\nOAuth app tokens and personal access tokens (classic) need the `security_events` scope to use this endpoint with private or public repositories, or the `public_repo` scope to use this endpoint with only public repositories.",
    "tags": [
        "code-scanning"
    ],
    "operationId": "code-scanning/get-variant-analysis",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/code-scanning/code-scanning#get-the-summary-of-a-codeql-variant-analysis"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "name": "codeql_variant_analysis_id",
            "in": "path",
            "description": "The unique identifier of the variant analysis.",
            "schema": {
                "type": "integer"
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
                        "$ref": "#/components/schemas/code-scanning-variant-analysis"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/code-scanning-variant-analysis"
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

### `#/components/schemas/code-scanning-variant-analysis`

```json
{
    "title": "Variant Analysis",
    "description": "A run of a CodeQL query against one or more repositories.",
    "type": "object",
    "properties": {
        "id": {
            "type": "integer",
            "description": "The ID of the variant analysis."
        },
        "controller_repo": {
            "$ref": "#/components/schemas/simple-repository"
        },
        "actor": {
            "$ref": "#/components/schemas/simple-user"
        },
        "query_language": {
            "$ref": "#/components/schemas/code-scanning-variant-analysis-language"
        },
        "query_pack_url": {
            "type": "string",
            "description": "The download url for the query pack."
        },
        "created_at": {
            "type": "string",
            "format": "date-time",
            "description": "The date and time at which the variant analysis was created, in ISO 8601 format':' YYYY-MM-DDTHH:MM:SSZ."
        },
        "updated_at": {
            "type": "string",
            "format": "date-time",
            "description": "The date and time at which the variant analysis was last updated, in ISO 8601 format':' YYYY-MM-DDTHH:MM:SSZ."
        },
        "completed_at": {
            "type": "string",
            "format": "date-time",
            "nullable": true,
            "description": "The date and time at which the variant analysis was completed, in ISO 8601 format':' YYYY-MM-DDTHH:MM:SSZ. Will be null if the variant analysis has not yet completed or this information is not available."
        },
        "status": {
            "type": "string",
            "enum": [
                "in_progress",
                "succeeded",
                "failed",
                "cancelled"
            ]
        },
        "actions_workflow_run_id": {
            "type": "integer",
            "description": "The GitHub Actions workflow run used to execute this variant analysis. This is only available if the workflow run has started."
        },
        "failure_reason": {
            "type": "string",
            "enum": [
                "no_repos_queried",
                "actions_workflow_run_failed",
                "internal_error"
            ],
            "description": "The reason for a failure of the variant analysis. This is only available if the variant analysis has failed."
        },
        "scanned_repositories": {
            "type": "array",
            "items": {
                "type": "object",
                "properties": {
                    "repository": {
                        "$ref": "#/components/schemas/code-scanning-variant-analysis-repository"
                    },
                    "analysis_status": {
                        "$ref": "#/components/schemas/code-scanning-variant-analysis-status"
                    },
                    "result_count": {
                        "type": "integer",
                        "description": "The number of results in the case of a successful analysis. This is only available for successful analyses."
                    },
                    "artifact_size_in_bytes": {
                        "type": "integer",
                        "description": "The size of the artifact. This is only available for successful analyses."
                    },
                    "failure_message": {
                        "type": "string",
                        "description": "The reason of the failure of this repo task. This is only available if the repository task has failed."
                    }
                },
                "required": [
                    "repository",
                    "analysis_status"
                ]
            }
        },
        "skipped_repositories": {
            "type": "object",
            "description": "Information about repositories that were skipped from processing. This information is only available to the user that initiated the variant analysis.",
            "properties": {
                "access_mismatch_repos": {
                    "$ref": "#/components/schemas/code-scanning-variant-analysis-skipped-repo-group"
                },
                "not_found_repos": {
                    "type": "object",
                    "properties": {
                        "repository_count": {
                            "type": "integer",
                            "description": "The total number of repositories that were skipped for this reason.",
                            "example": 2
                        },
                        "repository_full_names": {
                            "type": "array",
                            "description": "A list of full repository names that were skipped. This list may not include all repositories that were skipped.",
                            "items": {
                                "type": "string"
                            }
                        }
                    },
                    "required": [
                        "repository_count",
                        "repository_full_names"
                    ]
                },
                "no_codeql_db_repos": {
                    "$ref": "#/components/schemas/code-scanning-variant-analysis-skipped-repo-group"
                },
                "over_limit_repos": {
                    "$ref": "#/components/schemas/code-scanning-variant-analysis-skipped-repo-group"
                }
            },
            "required": [
                "access_mismatch_repos",
                "not_found_repos",
                "no_codeql_db_repos",
                "over_limit_repos"
            ]
        }
    },
    "required": [
        "id",
        "controller_repo",
        "actor",
        "query_language",
        "query_pack_url",
        "status"
    ]
}
```

### `#/components/examples/code-scanning-variant-analysis`

```json
{
    "summary": "Default response",
    "value": {
        "id": 1,
        "controller_repo": {
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
        "query_language": "python",
        "query_pack_url": "https://www.example.com",
        "created_at": "2022-09-12T12:14:32Z",
        "updated_at": "2022-09-12T12:14:32Z",
        "completed_at": "2022-09-12T13:15:33Z",
        "status": "completed",
        "actions_workflow_run_id": 3453588,
        "scanned_repositories": [
            {
                "repository": {
                    "id": 1296269,
                    "name": "Hello-World",
                    "full_name": "octocat/Hello-World",
                    "private": false
                },
                "analysis_status": "succeeded",
                "result_count": 532,
                "artifact_size_in_bytes": 12345
            }
        ],
        "skipped_repositories": {
            "access_mismatch_repos": {
                "repository_count": 2,
                "repositories": [
                    {
                        "id": 1,
                        "node_id": "MDQ6VXNlcjE=",
                        "name": "octo-repo1",
                        "full_name": "octo-org/octo-repo1",
                        "private": false
                    },
                    {
                        "id": 2,
                        "node_id": "MDQ6VXNlcjE=",
                        "name": "octo-repo2",
                        "full_name": "octo-org/octo-repo2",
                        "private": false
                    }
                ]
            },
            "not_found_repos": {
                "repository_count": 3,
                "repository_full_names": [
                    "octo-org/octo-repo4",
                    "octo-org/octo-repo5",
                    "octo-org/octo-repo6"
                ]
            },
            "no_codeql_db_repos": {
                "repository_count": 2,
                "repositories": [
                    {
                        "id": 7,
                        "node_id": "MDQ6VXNlcjE=",
                        "name": "octo-repo7",
                        "full_name": "octo-org/octo-repo7",
                        "private": false
                    },
                    {
                        "id": 8,
                        "node_id": "MDQ6VXNlcjE=",
                        "name": "octo-repo8",
                        "full_name": "octo-org/octo-repo8",
                        "private": false
                    }
                ]
            },
            "over_limit_repos": {
                "repository_count": 2,
                "repositories": [
                    {
                        "id": 9,
                        "node_id": "MDQ6VXNlcjE=",
                        "name": "octo-repo9",
                        "full_name": "octo-org/octo-repo9",
                        "private": false
                    },
                    {
                        "id": 10,
                        "node_id": "MDQ6VXNlcjE=",
                        "name": "octo-repo10",
                        "full_name": "octo-org/octo-repo10",
                        "private": false
                    }
                ]
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