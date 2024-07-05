# List repositories accessible to the user access token

List repositories that the authenticated user has explicit permission (`:read`, `:write`, or `:admin`) to access for an installation.

The authenticated user has explicit permission to access repositories they own, repositories where they are a collaborator, and repositories that they can access through an organization membership.

The access the user has to each repository is included in the hash under the `permissions` key.

## Operation Object

```json
{
    "summary": "List repositories accessible to the user access token",
    "description": "List repositories that the authenticated user has explicit permission (`:read`, `:write`, or `:admin`) to access for an installation.\n\nThe authenticated user has explicit permission to access repositories they own, repositories where they are a collaborator, and repositories that they can access through an organization membership.\n\nThe access the user has to each repository is included in the hash under the `permissions` key.",
    "tags": [
        "apps"
    ],
    "operationId": "apps/list-installation-repos-for-authenticated-user",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/apps/installations#list-repositories-accessible-to-the-user-access-token"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/installation-id"
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
            "description": "The access the user has to each repository is included in the hash under the `permissions` key.",
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
                            "repository_selection": {
                                "type": "string"
                            },
                            "repositories": {
                                "type": "array",
                                "items": {
                                    "$ref": "#/components/schemas/repository"
                                }
                            }
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/repository-paginated"
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
        "403": {
            "$ref": "#/components/responses/forbidden"
        },
        "304": {
            "$ref": "#/components/responses/not_modified"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": false,
        "category": "apps",
        "subcategory": "installations"
    }
}
```

## References

### `#/components/parameters/installation-id`

```json
{
    "name": "installation_id",
    "description": "The unique identifier of the installation.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "integer"
    },
    "examples": {
        "default": {
            "value": 1
        }
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

### `#/components/schemas/repository`

```json
{
    "title": "Repository",
    "description": "A repository on GitHub.",
    "type": "object",
    "properties": {
        "id": {
            "description": "Unique identifier of the repository",
            "example": 42,
            "type": "integer",
            "format": "int64"
        },
        "node_id": {
            "type": "string",
            "example": "MDEwOlJlcG9zaXRvcnkxMjk2MjY5"
        },
        "name": {
            "description": "The name of the repository.",
            "type": "string",
            "example": "Team Environment"
        },
        "full_name": {
            "type": "string",
            "example": "octocat/Hello-World"
        },
        "license": {
            "$ref": "#/components/schemas/nullable-license-simple"
        },
        "forks": {
            "type": "integer"
        },
        "permissions": {
            "type": "object",
            "properties": {
                "admin": {
                    "type": "boolean"
                },
                "pull": {
                    "type": "boolean"
                },
                "triage": {
                    "type": "boolean"
                },
                "push": {
                    "type": "boolean"
                },
                "maintain": {
                    "type": "boolean"
                }
            },
            "required": [
                "admin",
                "pull",
                "push"
            ]
        },
        "owner": {
            "$ref": "#/components/schemas/simple-user"
        },
        "private": {
            "description": "Whether the repository is private or public.",
            "default": false,
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
            "type": "string",
            "example": "git:github.com/octocat/Hello-World.git"
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
            "type": "string",
            "example": "git@github.com:octocat/Hello-World.git"
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
            "type": "string",
            "example": "https://github.com/octocat/Hello-World.git"
        },
        "mirror_url": {
            "type": "string",
            "format": "uri",
            "example": "git:git.example.com/octocat/Hello-World",
            "nullable": true
        },
        "hooks_url": {
            "type": "string",
            "format": "uri",
            "example": "http://api.github.com/repos/octocat/Hello-World/hooks"
        },
        "svn_url": {
            "type": "string",
            "format": "uri",
            "example": "https://svn.github.com/octocat/Hello-World"
        },
        "homepage": {
            "type": "string",
            "format": "uri",
            "example": "https://github.com",
            "nullable": true
        },
        "language": {
            "type": "string",
            "nullable": true
        },
        "forks_count": {
            "type": "integer",
            "example": 9
        },
        "stargazers_count": {
            "type": "integer",
            "example": 80
        },
        "watchers_count": {
            "type": "integer",
            "example": 80
        },
        "size": {
            "description": "The size of the repository, in kilobytes. Size is calculated hourly. When a repository is initially created, the size is 0.",
            "type": "integer",
            "example": 108
        },
        "default_branch": {
            "description": "The default branch of the repository.",
            "type": "string",
            "example": "master"
        },
        "open_issues_count": {
            "type": "integer",
            "example": 0
        },
        "is_template": {
            "description": "Whether this repository acts as a template that can be used to generate new repositories.",
            "default": false,
            "type": "boolean",
            "example": true
        },
        "topics": {
            "type": "array",
            "items": {
                "type": "string"
            }
        },
        "has_issues": {
            "description": "Whether issues are enabled.",
            "default": true,
            "type": "boolean",
            "example": true
        },
        "has_projects": {
            "description": "Whether projects are enabled.",
            "default": true,
            "type": "boolean",
            "example": true
        },
        "has_wiki": {
            "description": "Whether the wiki is enabled.",
            "default": true,
            "type": "boolean",
            "example": true
        },
        "has_pages": {
            "type": "boolean"
        },
        "has_downloads": {
            "description": "Whether downloads are enabled.",
            "default": true,
            "type": "boolean",
            "example": true,
            "deprecated": true
        },
        "has_discussions": {
            "description": "Whether discussions are enabled.",
            "default": false,
            "type": "boolean",
            "example": true
        },
        "archived": {
            "description": "Whether the repository is archived.",
            "default": false,
            "type": "boolean"
        },
        "disabled": {
            "type": "boolean",
            "description": "Returns whether or not this repository disabled."
        },
        "visibility": {
            "description": "The repository visibility: public, private, or internal.",
            "default": "public",
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
        "allow_rebase_merge": {
            "description": "Whether to allow rebase merges for pull requests.",
            "default": true,
            "type": "boolean",
            "example": true
        },
        "temp_clone_token": {
            "type": "string"
        },
        "allow_squash_merge": {
            "description": "Whether to allow squash merges for pull requests.",
            "default": true,
            "type": "boolean",
            "example": true
        },
        "allow_auto_merge": {
            "description": "Whether to allow Auto-merge to be used on pull requests.",
            "default": false,
            "type": "boolean",
            "example": false
        },
        "delete_branch_on_merge": {
            "description": "Whether to delete head branches when pull requests are merged",
            "default": false,
            "type": "boolean",
            "example": false
        },
        "allow_update_branch": {
            "description": "Whether or not a pull request head branch that is behind its base branch can always be updated even if it is not required to be up to date before merging.",
            "default": false,
            "type": "boolean",
            "example": false
        },
        "use_squash_pr_title_as_default": {
            "type": "boolean",
            "description": "Whether a squash merge commit can use the pull request title as default. **This property has been deprecated. Please use `squash_merge_commit_title` instead.",
            "default": false,
            "deprecated": true
        },
        "squash_merge_commit_title": {
            "type": "string",
            "enum": [
                "PR_TITLE",
                "COMMIT_OR_PR_TITLE"
            ],
            "description": "The default value for a squash merge commit title:\n\n- `PR_TITLE` - default to the pull request's title.\n- `COMMIT_OR_PR_TITLE` - default to the commit's title (if only one commit) or the pull request's title (when more than one commit)."
        },
        "squash_merge_commit_message": {
            "type": "string",
            "enum": [
                "PR_BODY",
                "COMMIT_MESSAGES",
                "BLANK"
            ],
            "description": "The default value for a squash merge commit message:\n\n- `PR_BODY` - default to the pull request's body.\n- `COMMIT_MESSAGES` - default to the branch's commit messages.\n- `BLANK` - default to a blank commit message."
        },
        "merge_commit_title": {
            "type": "string",
            "enum": [
                "PR_TITLE",
                "MERGE_MESSAGE"
            ],
            "description": "The default value for a merge commit title.\n\n- `PR_TITLE` - default to the pull request's title.\n- `MERGE_MESSAGE` - default to the classic title for a merge message (e.g., Merge pull request #123 from branch-name)."
        },
        "merge_commit_message": {
            "type": "string",
            "enum": [
                "PR_BODY",
                "PR_TITLE",
                "BLANK"
            ],
            "description": "The default value for a merge commit message.\n\n- `PR_TITLE` - default to the pull request's title.\n- `PR_BODY` - default to the pull request's body.\n- `BLANK` - default to a blank commit message."
        },
        "allow_merge_commit": {
            "description": "Whether to allow merge commits for pull requests.",
            "default": true,
            "type": "boolean",
            "example": true
        },
        "allow_forking": {
            "description": "Whether to allow forking this repo",
            "type": "boolean"
        },
        "web_commit_signoff_required": {
            "description": "Whether to require contributors to sign off on web-based commits",
            "default": false,
            "type": "boolean"
        },
        "open_issues": {
            "type": "integer"
        },
        "watchers": {
            "type": "integer"
        },
        "master_branch": {
            "type": "string"
        },
        "starred_at": {
            "type": "string",
            "example": "\"2020-07-09T00:17:42Z\""
        },
        "anonymous_access_enabled": {
            "type": "boolean",
            "description": "Whether anonymous git access is enabled for this repository"
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
        "url",
        "clone_url",
        "default_branch",
        "forks",
        "forks_count",
        "git_url",
        "has_downloads",
        "has_issues",
        "has_projects",
        "has_wiki",
        "has_pages",
        "homepage",
        "language",
        "archived",
        "disabled",
        "mirror_url",
        "open_issues",
        "open_issues_count",
        "license",
        "pushed_at",
        "size",
        "ssh_url",
        "stargazers_count",
        "svn_url",
        "watchers",
        "watchers_count",
        "created_at",
        "updated_at"
    ]
}
```

### `#/components/examples/repository-paginated`

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

### `#/components/responses/forbidden`

```json
{
    "description": "Forbidden",
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