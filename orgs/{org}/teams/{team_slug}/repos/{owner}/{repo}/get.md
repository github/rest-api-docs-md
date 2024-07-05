# Check team permissions for a repository

Checks whether a team has `admin`, `push`, `maintain`, `triage`, or `pull` permission for a repository. Repositories inherited through a parent team will also be checked.

You can also get information about the specified repository, including what permissions the team grants on it, by passing the following custom [media type](https://docs.github.com/rest/using-the-rest-api/getting-started-with-the-rest-api#media-types/) via the `application/vnd.github.v3.repository+json` accept header.

If a team doesn't have permission for the repository, you will receive a `404 Not Found` response status.

If the repository is private, you must have at least `read` permission for that repository, and your token must have the `repo` or `admin:org` scope. Otherwise, you will receive a `404 Not Found` response status.

**Note:** You can also specify a team by `org_id` and `team_id` using the route `GET /organizations/{org_id}/team/{team_id}/repos/{owner}/{repo}`.

## Operation Object

```json
{
    "summary": "Check team permissions for a repository",
    "description": "Checks whether a team has `admin`, `push`, `maintain`, `triage`, or `pull` permission for a repository. Repositories inherited through a parent team will also be checked.\n\nYou can also get information about the specified repository, including what permissions the team grants on it, by passing the following custom [media type](https://docs.github.com/rest/using-the-rest-api/getting-started-with-the-rest-api#media-types/) via the `application/vnd.github.v3.repository+json` accept header.\n\nIf a team doesn't have permission for the repository, you will receive a `404 Not Found` response status.\n\nIf the repository is private, you must have at least `read` permission for that repository, and your token must have the `repo` or `admin:org` scope. Otherwise, you will receive a `404 Not Found` response status.\n\n**Note:** You can also specify a team by `org_id` and `team_id` using the route `GET /organizations/{org_id}/team/{team_id}/repos/{owner}/{repo}`.",
    "tags": [
        "teams"
    ],
    "operationId": "teams/check-permissions-for-repo-in-org",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/teams/teams#check-team-permissions-for-a-repository"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/org"
        },
        {
            "$ref": "#/components/parameters/team-slug"
        },
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        }
    ],
    "responses": {
        "200": {
            "description": "Alternative response with repository permissions",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/team-repository"
                    },
                    "examples": {
                        "alternative-response-with-repository-permissions": {
                            "$ref": "#/components/examples/team-repository-alternative-response-with-repository-permissions"
                        }
                    }
                }
            }
        },
        "204": {
            "description": "Response if team has permission for the repository. This is the response when the repository media type hasn't been provded in the Accept header."
        },
        "404": {
            "description": "Not Found if team does not have permission for the repository"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "teams",
        "subcategory": "teams"
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

### `#/components/parameters/team-slug`

```json
{
    "name": "team_slug",
    "description": "The slug of the team name.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "string"
    }
}
```

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

### `#/components/schemas/team-repository`

```json
{
    "title": "Team Repository",
    "description": "A team's access to a repository.",
    "type": "object",
    "properties": {
        "id": {
            "description": "Unique identifier of the repository",
            "example": 42,
            "type": "integer"
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
        "role_name": {
            "type": "string",
            "example": "admin"
        },
        "owner": {
            "$ref": "#/components/schemas/nullable-simple-user"
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
        "allow_merge_commit": {
            "description": "Whether to allow merge commits for pull requests.",
            "default": true,
            "type": "boolean",
            "example": true
        },
        "allow_forking": {
            "description": "Whether to allow forking this repo",
            "default": false,
            "type": "boolean",
            "example": false
        },
        "web_commit_signoff_required": {
            "description": "Whether to require contributors to sign off on web-based commits",
            "default": false,
            "type": "boolean",
            "example": false
        },
        "subscribers_count": {
            "type": "integer"
        },
        "network_count": {
            "type": "integer"
        },
        "open_issues": {
            "type": "integer"
        },
        "watchers": {
            "type": "integer"
        },
        "master_branch": {
            "type": "string"
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

### `#/components/examples/team-repository-alternative-response-with-repository-permissions`

```json
{
    "value": {
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
        "is_template": false,
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
            "maintain": false,
            "push": false,
            "triage": false,
            "pull": true
        },
        "role_name": "read",
        "allow_rebase_merge": true,
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
            "html_url": "https://api.github.com/licenses/mit"
        },
        "forks": 1,
        "open_issues": 1,
        "watchers": 1
    }
}
```