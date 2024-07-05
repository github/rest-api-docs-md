# Get a package for the authenticated user

Gets a specific package for a package owned by the authenticated user.

OAuth app tokens and personal access tokens (classic) need the `read:packages` scope to use this endpoint. If the `package_type` belongs to a GitHub Packages registry that only supports repository-scoped permissions, the `repo` scope is also required. For the list of these registries, see "[About permissions for GitHub Packages](https://docs.github.com/packages/learn-github-packages/about-permissions-for-github-packages#permissions-for-repository-scoped-packages)."

## Operation Object

```json
{
    "summary": "Get a package for the authenticated user",
    "description": "Gets a specific package for a package owned by the authenticated user.\n\nOAuth app tokens and personal access tokens (classic) need the `read:packages` scope to use this endpoint. If the `package_type` belongs to a GitHub Packages registry that only supports repository-scoped permissions, the `repo` scope is also required. For the list of these registries, see \"[About permissions for GitHub Packages](https://docs.github.com/packages/learn-github-packages/about-permissions-for-github-packages#permissions-for-repository-scoped-packages).\"",
    "tags": [
        "packages"
    ],
    "operationId": "packages/get-package-for-authenticated-user",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/packages/packages#get-a-package-for-the-authenticated-user"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/package-type"
        },
        {
            "$ref": "#/components/parameters/package-name"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/package"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/package-user"
                        }
                    }
                }
            }
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": false,
        "category": "packages",
        "subcategory": "packages"
    }
}
```

## References

### `#/components/parameters/package-type`

```json
{
    "name": "package_type",
    "description": "The type of supported package. Packages in GitHub's Gradle registry have the type `maven`. Docker images pushed to GitHub's Container registry (`ghcr.io`) have the type `container`. You can use the type `docker` to find images that were pushed to GitHub's Docker registry (`docker.pkg.github.com`), even if these have now been migrated to the Container registry.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "string",
        "enum": [
            "npm",
            "maven",
            "rubygems",
            "docker",
            "nuget",
            "container"
        ]
    }
}
```

### `#/components/parameters/package-name`

```json
{
    "name": "package_name",
    "description": "The name of the package.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "string"
    }
}
```

### `#/components/schemas/package`

```json
{
    "title": "Package",
    "description": "A software package",
    "type": "object",
    "properties": {
        "id": {
            "description": "Unique identifier of the package.",
            "type": "integer",
            "example": 1
        },
        "name": {
            "description": "The name of the package.",
            "type": "string",
            "example": "super-linter"
        },
        "package_type": {
            "type": "string",
            "example": "docker",
            "enum": [
                "npm",
                "maven",
                "rubygems",
                "docker",
                "nuget",
                "container"
            ]
        },
        "url": {
            "type": "string",
            "example": "https://api.github.com/orgs/github/packages/container/super-linter"
        },
        "html_url": {
            "type": "string",
            "example": "https://github.com/orgs/github/packages/container/package/super-linter"
        },
        "version_count": {
            "description": "The number of versions of the package.",
            "type": "integer",
            "example": 1
        },
        "visibility": {
            "type": "string",
            "example": "private",
            "enum": [
                "private",
                "public"
            ]
        },
        "owner": {
            "$ref": "#/components/schemas/nullable-simple-user"
        },
        "repository": {
            "$ref": "#/components/schemas/nullable-minimal-repository"
        },
        "created_at": {
            "type": "string",
            "format": "date-time"
        },
        "updated_at": {
            "type": "string",
            "format": "date-time"
        }
    },
    "required": [
        "id",
        "name",
        "package_type",
        "visibility",
        "url",
        "html_url",
        "version_count",
        "created_at",
        "updated_at"
    ]
}
```

### `#/components/examples/package-user`

```json
{
    "value": {
        "id": 40201,
        "name": "octo-name",
        "package_type": "rubygems",
        "owner": {
            "login": "octocat",
            "id": 209477,
            "node_id": "MDQ6VXNlcjIwOTQ3Nw==",
            "avatar_url": "https://avatars.githubusercontent.com/u/209477?v=4",
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
            "site_admin": true
        },
        "version_count": 3,
        "visibility": "public",
        "url": "https://api.github.com/users/octocat/packages/rubygems/octo-name",
        "created_at": "2019-10-20T14:17:14Z",
        "updated_at": "2019-10-20T14:17:14Z",
        "repository": {
            "id": 216219492,
            "node_id": "MDEwOlJlcG9zaXRvcnkyMTYyMTk0OTI=",
            "name": "octo-name-repo",
            "full_name": "octocat/octo-name-repo",
            "private": false,
            "owner": {
                "login": "octocat",
                "id": 209477,
                "node_id": "MDQ6VXNlcjIwOTQ3Nw==",
                "avatar_url": "https://avatars.githubusercontent.com/u/209477?v=4",
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
                "site_admin": true
            },
            "html_url": "https://github.com/octocat/octo-name-repo",
            "description": "Project for octocats",
            "fork": false,
            "url": "https://api.github.com/repos/octocat/octo-name-repo",
            "forks_url": "https://api.github.com/repos/octocat/octo-name-repo/forks",
            "keys_url": "https://api.github.com/repos/octocat/octo-name-repo/keys{/key_id}",
            "collaborators_url": "https://api.github.com/repos/octocat/octo-name-repo/collaborators{/collaborator}",
            "teams_url": "https://api.github.com/repos/octocat/octo-name-repo/teams",
            "hooks_url": "https://api.github.com/repos/octocat/octo-name-repo/hooks",
            "issue_events_url": "https://api.github.com/repos/octocat/octo-name-repo/issues/events{/number}",
            "events_url": "https://api.github.com/repos/octocat/octo-name-repo/events",
            "assignees_url": "https://api.github.com/repos/octocat/octo-name-repo/assignees{/user}",
            "branches_url": "https://api.github.com/repos/octocat/octo-name-repo/branches{/branch}",
            "tags_url": "https://api.github.com/repos/octocat/octo-name-repo/tags",
            "blobs_url": "https://api.github.com/repos/octocat/octo-name-repo/git/blobs{/sha}",
            "git_tags_url": "https://api.github.com/repos/octocat/octo-name-repo/git/tags{/sha}",
            "git_refs_url": "https://api.github.com/repos/octocat/octo-name-repo/git/refs{/sha}",
            "trees_url": "https://api.github.com/repos/octocat/octo-name-repo/git/trees{/sha}",
            "statuses_url": "https://api.github.com/repos/octocat/octo-name-repo/statuses/{sha}",
            "languages_url": "https://api.github.com/repos/octocat/octo-name-repo/languages",
            "stargazers_url": "https://api.github.com/repos/octocat/octo-name-repo/stargazers",
            "contributors_url": "https://api.github.com/repos/octocat/octo-name-repo/contributors",
            "subscribers_url": "https://api.github.com/repos/octocat/octo-name-repo/subscribers",
            "subscription_url": "https://api.github.com/repos/octocat/octo-name-repo/subscription",
            "commits_url": "https://api.github.com/repos/octocat/octo-name-repo/commits{/sha}",
            "git_commits_url": "https://api.github.com/repos/octocat/octo-name-repo/git/commits{/sha}",
            "comments_url": "https://api.github.com/repos/octocat/octo-name-repo/comments{/number}",
            "issue_comment_url": "https://api.github.com/repos/octocat/octo-name-repo/issues/comments{/number}",
            "contents_url": "https://api.github.com/repos/octocat/octo-name-repo/contents/{+path}",
            "compare_url": "https://api.github.com/repos/octocat/octo-name-repo/compare/{base}...{head}",
            "merges_url": "https://api.github.com/repos/octocat/octo-name-repo/merges",
            "archive_url": "https://api.github.com/repos/octocat/octo-name-repo/{archive_format}{/ref}",
            "downloads_url": "https://api.github.com/repos/octocat/octo-name-repo/downloads",
            "issues_url": "https://api.github.com/repos/octocat/octo-name-repo/issues{/number}",
            "pulls_url": "https://api.github.com/repos/octocat/octo-name-repo/pulls{/number}",
            "milestones_url": "https://api.github.com/repos/octocat/octo-name-repo/milestones{/number}",
            "notifications_url": "https://api.github.com/repos/octocat/octo-name-repo/notifications{?since,all,participating}",
            "labels_url": "https://api.github.com/repos/octocat/octo-name-repo/labels{/name}",
            "releases_url": "https://api.github.com/repos/octocat/octo-name-repo/releases{/id}",
            "deployments_url": "https://api.github.com/repos/octocat/octo-name-repo/deployments"
        },
        "html_url": "https://github.com/octocat/octo-name-repo/packages/40201"
    }
}
```