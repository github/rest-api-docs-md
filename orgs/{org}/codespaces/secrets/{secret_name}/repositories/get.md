# List selected repositories for an organization secret

`get /orgs/{org}/codespaces/secrets/{secret_name}/repositories`

Lists all repositories that have been selected when the `visibility`
for repository access to a secret is set to `selected`.

OAuth app tokens and personal access tokens (classic) need the `admin:org` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "List selected repositories for an organization secret",
    "description": "Lists all repositories that have been selected when the `visibility`\nfor repository access to a secret is set to `selected`.\n\nOAuth app tokens and personal access tokens (classic) need the `admin:org` scope to use this endpoint.",
    "tags": [
        "codespaces"
    ],
    "operationId": "codespaces/list-selected-repos-for-org-secret",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/codespaces/organization-secrets#list-selected-repositories-for-an-organization-secret"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/org"
        },
        {
            "$ref": "#/components/parameters/secret-name"
        },
        {
            "$ref": "#/components/parameters/page"
        },
        {
            "$ref": "#/components/parameters/per-page"
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
                            "repositories"
                        ],
                        "properties": {
                            "total_count": {
                                "type": "integer"
                            },
                            "repositories": {
                                "type": "array",
                                "items": {
                                    "$ref": "#/components/schemas/minimal-repository"
                                }
                            }
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/public-repository-paginated"
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
        "enabledForGitHubApps": false,
        "category": "codespaces",
        "subcategory": "organization-secrets"
    }
}
```

## References

### `#/components/parameters/org`

```json
{
    "name": "org",
    "description": "The organization name. The name is not case sensitive.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "string"
    }
}
```

### `#/components/parameters/secret-name`

```json
{
    "name": "secret_name",
    "description": "The name of the secret.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "string"
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

### `#/components/schemas/minimal-repository`

```json
{
    "title": "Minimal Repository",
    "description": "Minimal Repository",
    "type": "object",
    "properties": {
        "id": {
            "type": "integer",
            "format": "int64",
            "example": 1296269
        },
        "node_id": {
            "type": "string",
            "example": "MDEwOlJlcG9zaXRvcnkxMjk2MjY5"
        },
        "name": {
            "type": "string",
            "example": "Hello-World"
        },
        "full_name": {
            "type": "string",
            "example": "octocat/Hello-World"
        },
        "owner": {
            "$ref": "#/components/schemas/simple-user"
        },
        "private": {
            "type": "boolean"
        },
        "html_url": {
            "type": "string",
            "format": "uri",
            "example": "https://github.com/octocat/Hello-World"
        },
        "description": {
            "type": "string",
            "example": "This your first repo!",
            "nullable": true
        },
        "fork": {
            "type": "boolean"
        },
        "url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/repos/octocat/Hello-World"
        },
        "archive_url": {
            "type": "string",
            "example": "http://api.github.com/repos/octocat/Hello-World/{archive_format}{/ref}"
        },
        "assignees_url": {
            "type": "string",
            "example": "http://api.github.com/repos/octocat/Hello-World/assignees{/user}"
        },
        "blobs_url": {
            "type": "string",
            "example": "http://api.github.com/repos/octocat/Hello-World/git/blobs{/sha}"
        },
        "branches_url": {
            "type": "string",
            "example": "http://api.github.com/repos/octocat/Hello-World/branches{/branch}"
        },
        "collaborators_url": {
            "type": "string",
            "example": "http://api.github.com/repos/octocat/Hello-World/collaborators{/collaborator}"
        },
        "comments_url": {
            "type": "string",
            "example": "http://api.github.com/repos/octocat/Hello-World/comments{/number}"
        },
        "commits_url": {
            "type": "string",
            "example": "http://api.github.com/repos/octocat/Hello-World/commits{/sha}"
        },
        "compare_url": {
            "type": "string",
            "example": "http://api.github.com/repos/octocat/Hello-World/compare/{base}...{head}"
        },
        "contents_url": {
            "type": "string",
            "example": "http://api.github.com/repos/octocat/Hello-World/contents/{+path}"
        },
        "contributors_url": {
            "type": "string",
            "format": "uri",
            "example": "http://api.github.com/repos/octocat/Hello-World/contributors"
        },
        "deployments_url": {
            "type": "string",
            "format": "uri",
            "example": "http://api.github.com/repos/octocat/Hello-World/deployments"
        },
        "downloads_url": {
            "type": "string",
            "format": "uri",
            "example": "http://api.github.com/repos/octocat/Hello-World/downloads"
        },
        "events_url": {
            "type": "string",
            "format": "uri",
            "example": "http://api.github.com/repos/octocat/Hello-World/events"
        },
        "forks_url": {
            "type": "string",
            "format": "uri",
            "example": "http://api.github.com/repos/octocat/Hello-World/forks"
        },
        "git_commits_url": {
            "type": "string",
            "example": "http://api.github.com/repos/octocat/Hello-World/git/commits{/sha}"
        },
        "git_refs_url": {
            "type": "string",
            "example": "http://api.github.com/repos/octocat/Hello-World/git/refs{/sha}"
        },
        "git_tags_url": {
            "type": "string",
            "example": "http://api.github.com/repos/octocat/Hello-World/git/tags{/sha}"
        },
        "git_url": {
            "type": "string"
        },
        "issue_comment_url": {
            "type": "string",
            "example": "http://api.github.com/repos/octocat/Hello-World/issues/comments{/number}"
        },
        "issue_events_url": {
            "type": "string",
            "example": "http://api.github.com/repos/octocat/Hello-World/issues/events{/number}"
        },
        "issues_url": {
            "type": "string",
            "example": "http://api.github.com/repos/octocat/Hello-World/issues{/number}"
        },
        "keys_url": {
            "type": "string",
            "example": "http://api.github.com/repos/octocat/Hello-World/keys{/key_id}"
        },
        "labels_url": {
            "type": "string",
            "example": "http://api.github.com/repos/octocat/Hello-World/labels{/name}"
        },
        "languages_url": {
            "type": "string",
            "format": "uri",
            "example": "http://api.github.com/repos/octocat/Hello-World/languages"
        },
        "merges_url": {
            "type": "string",
            "format": "uri",
            "example": "http://api.github.com/repos/octocat/Hello-World/merges"
        },
        "milestones_url": {
            "type": "string",
            "example": "http://api.github.com/repos/octocat/Hello-World/milestones{/number}"
        },
        "notifications_url": {
            "type": "string",
            "example": "http://api.github.com/repos/octocat/Hello-World/notifications{?since,all,participating}"
        },
        "pulls_url": {
            "type": "string",
            "example": "http://api.github.com/repos/octocat/Hello-World/pulls{/number}"
        },
        "releases_url": {
            "type": "string",
            "example": "http://api.github.com/repos/octocat/Hello-World/releases{/id}"
        },
        "ssh_url": {
            "type": "string"
        },
        "stargazers_url": {
            "type": "string",
            "format": "uri",
            "example": "http://api.github.com/repos/octocat/Hello-World/stargazers"
        },
        "statuses_url": {
            "type": "string",
            "example": "http://api.github.com/repos/octocat/Hello-World/statuses/{sha}"
        },
        "subscribers_url": {
            "type": "string",
            "format": "uri",
            "example": "http://api.github.com/repos/octocat/Hello-World/subscribers"
        },
        "subscription_url": {
            "type": "string",
            "format": "uri",
            "example": "http://api.github.com/repos/octocat/Hello-World/subscription"
        },
        "tags_url": {
            "type": "string",
            "format": "uri",
            "example": "http://api.github.com/repos/octocat/Hello-World/tags"
        },
        "teams_url": {
            "type": "string",
            "format": "uri",
            "example": "http://api.github.com/repos/octocat/Hello-World/teams"
        },
        "trees_url": {
            "type": "string",
            "example": "http://api.github.com/repos/octocat/Hello-World/git/trees{/sha}"
        },
        "clone_url": {
            "type": "string"
        },
        "mirror_url": {
            "type": "string",
            "nullable": true
        },
        "hooks_url": {
            "type": "string",
            "format": "uri",
            "example": "http://api.github.com/repos/octocat/Hello-World/hooks"
        },
        "svn_url": {
            "type": "string"
        },
        "homepage": {
            "type": "string",
            "nullable": true
        },
        "language": {
            "type": "string",
            "nullable": true
        },
        "forks_count": {
            "type": "integer"
        },
        "stargazers_count": {
            "type": "integer"
        },
        "watchers_count": {
            "type": "integer"
        },
        "size": {
            "description": "The size of the repository, in kilobytes. Size is calculated hourly. When a repository is initially created, the size is 0.",
            "type": "integer"
        },
        "default_branch": {
            "type": "string"
        },
        "open_issues_count": {
            "type": "integer"
        },
        "is_template": {
            "type": "boolean"
        },
        "topics": {
            "type": "array",
            "items": {
                "type": "string"
            }
        },
        "has_issues": {
            "type": "boolean"
        },
        "has_projects": {
            "type": "boolean"
        },
        "has_wiki": {
            "type": "boolean"
        },
        "has_pages": {
            "type": "boolean"
        },
        "has_downloads": {
            "type": "boolean"
        },
        "has_discussions": {
            "type": "boolean"
        },
        "archived": {
            "type": "boolean"
        },
        "disabled": {
            "type": "boolean"
        },
        "visibility": {
            "type": "string"
        },
        "pushed_at": {
            "type": "string",
            "format": "date-time",
            "example": "2011-01-26T19:06:43Z",
            "nullable": true
        },
        "created_at": {
            "type": "string",
            "format": "date-time",
            "example": "2011-01-26T19:01:12Z",
            "nullable": true
        },
        "updated_at": {
            "type": "string",
            "format": "date-time",
            "example": "2011-01-26T19:14:43Z",
            "nullable": true
        },
        "permissions": {
            "type": "object",
            "properties": {
                "admin": {
                    "type": "boolean"
                },
                "maintain": {
                    "type": "boolean"
                },
                "push": {
                    "type": "boolean"
                },
                "triage": {
                    "type": "boolean"
                },
                "pull": {
                    "type": "boolean"
                }
            }
        },
        "role_name": {
            "type": "string",
            "example": "admin"
        },
        "temp_clone_token": {
            "type": "string"
        },
        "delete_branch_on_merge": {
            "type": "boolean"
        },
        "subscribers_count": {
            "type": "integer"
        },
        "network_count": {
            "type": "integer"
        },
        "code_of_conduct": {
            "$ref": "#/components/schemas/code-of-conduct"
        },
        "license": {
            "type": "object",
            "properties": {
                "key": {
                    "type": "string"
                },
                "name": {
                    "type": "string"
                },
                "spdx_id": {
                    "type": "string"
                },
                "url": {
                    "type": "string"
                },
                "node_id": {
                    "type": "string"
                }
            },
            "nullable": true
        },
        "forks": {
            "type": "integer",
            "example": 0
        },
        "open_issues": {
            "type": "integer",
            "example": 0
        },
        "watchers": {
            "type": "integer",
            "example": 0
        },
        "allow_forking": {
            "type": "boolean"
        },
        "web_commit_signoff_required": {
            "type": "boolean",
            "example": false
        },
        "security_and_analysis": {
            "$ref": "#/components/schemas/security-and-analysis"
        }
    },
    "required": [
        "archive_url",
        "assignees_url",
        "blobs_url",
        "branches_url",
        "collaborators_url",
        "comments_url",
        "commits_url",
        "compare_url",
        "contents_url",
        "contributors_url",
        "deployments_url",
        "description",
        "downloads_url",
        "events_url",
        "fork",
        "forks_url",
        "full_name",
        "git_commits_url",
        "git_refs_url",
        "git_tags_url",
        "hooks_url",
        "html_url",
        "id",
        "node_id",
        "issue_comment_url",
        "issue_events_url",
        "issues_url",
        "keys_url",
        "labels_url",
        "languages_url",
        "merges_url",
        "milestones_url",
        "name",
        "notifications_url",
        "owner",
        "private",
        "pulls_url",
        "releases_url",
        "stargazers_url",
        "statuses_url",
        "subscribers_url",
        "subscription_url",
        "tags_url",
        "teams_url",
        "trees_url",
        "url"
    ]
}
```

### `#/components/examples/public-repository-paginated`

```json
{
    "value": {
        "total_count": 1,
        "repositories": [
            {
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
            }
        ]
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