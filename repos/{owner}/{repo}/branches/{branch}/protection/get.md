# Get branch protection

`get /repos/{owner}/{repo}/branches/{branch}/protection`

Protected branches are available in public repositories with GitHub Free and GitHub Free for organizations, and in public and private repositories with GitHub Pro, GitHub Team, GitHub Enterprise Cloud, and GitHub Enterprise Server. For more information, see [GitHub's products](https://docs.github.com/github/getting-started-with-github/githubs-products) in the GitHub Help documentation.

## Operation Object

```json
{
    "summary": "Get branch protection",
    "description": "Protected branches are available in public repositories with GitHub Free and GitHub Free for organizations, and in public and private repositories with GitHub Pro, GitHub Team, GitHub Enterprise Cloud, and GitHub Enterprise Server. For more information, see [GitHub's products](https://docs.github.com/github/getting-started-with-github/githubs-products) in the GitHub Help documentation.",
    "tags": [
        "repos"
    ],
    "operationId": "repos/get-branch-protection",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/branches/branch-protection#get-branch-protection"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "$ref": "#/components/parameters/branch"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/branch-protection"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/branch-protection"
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
        "category": "branches",
        "subcategory": "branch-protection"
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

### `#/components/parameters/branch`

```json
{
    "name": "branch",
    "description": "The name of the branch. Cannot contain wildcard characters. To use wildcard characters in branch names, use [the GraphQL API](https://docs.github.com/graphql).",
    "in": "path",
    "required": true,
    "schema": {
        "type": "string"
    },
    "x-multi-segment": true
}
```

### `#/components/schemas/branch-protection`

```json
{
    "title": "Branch Protection",
    "description": "Branch Protection",
    "type": "object",
    "properties": {
        "url": {
            "type": "string"
        },
        "enabled": {
            "type": "boolean"
        },
        "required_status_checks": {
            "$ref": "#/components/schemas/protected-branch-required-status-check"
        },
        "enforce_admins": {
            "$ref": "#/components/schemas/protected-branch-admin-enforced"
        },
        "required_pull_request_reviews": {
            "$ref": "#/components/schemas/protected-branch-pull-request-review"
        },
        "restrictions": {
            "$ref": "#/components/schemas/branch-restriction-policy"
        },
        "required_linear_history": {
            "type": "object",
            "properties": {
                "enabled": {
                    "type": "boolean"
                }
            }
        },
        "allow_force_pushes": {
            "type": "object",
            "properties": {
                "enabled": {
                    "type": "boolean"
                }
            }
        },
        "allow_deletions": {
            "type": "object",
            "properties": {
                "enabled": {
                    "type": "boolean"
                }
            }
        },
        "block_creations": {
            "type": "object",
            "properties": {
                "enabled": {
                    "type": "boolean"
                }
            }
        },
        "required_conversation_resolution": {
            "type": "object",
            "properties": {
                "enabled": {
                    "type": "boolean"
                }
            }
        },
        "name": {
            "type": "string",
            "example": "\"branch/with/protection\""
        },
        "protection_url": {
            "type": "string",
            "example": "\"https://api.github.com/repos/owner-79e94e2d36b3fd06a32bb213/AAA_Public_Repo/branches/branch/with/protection/protection\""
        },
        "required_signatures": {
            "type": "object",
            "properties": {
                "url": {
                    "type": "string",
                    "format": "uri",
                    "example": "https://api.github.com/repos/octocat/Hello-World/branches/master/protection/required_signatures"
                },
                "enabled": {
                    "type": "boolean",
                    "example": true
                }
            },
            "required": [
                "url",
                "enabled"
            ]
        },
        "lock_branch": {
            "type": "object",
            "description": "Whether to set the branch as read-only. If this is true, users will not be able to push to the branch.",
            "properties": {
                "enabled": {
                    "default": false,
                    "type": "boolean"
                }
            }
        },
        "allow_fork_syncing": {
            "type": "object",
            "description": "Whether users can pull changes from upstream when the branch is locked. Set to `true` to allow fork syncing. Set to `false` to prevent fork syncing.",
            "properties": {
                "enabled": {
                    "default": false,
                    "type": "boolean"
                }
            }
        }
    }
}
```

### `#/components/examples/branch-protection`

```json
{
    "value": {
        "url": "https://api.github.com/repos/octocat/Hello-World/branches/master/protection",
        "required_status_checks": {
            "url": "https://api.github.com/repos/octocat/Hello-World/branches/master/protection/required_status_checks",
            "contexts": [
                "continuous-integration/travis-ci"
            ],
            "contexts_url": "https://api.github.com/repos/octocat/Hello-World/branches/master/protection/required_status_checks/contexts",
            "enforcement_level": "non_admins"
        },
        "enforce_admins": {
            "url": "https://api.github.com/repos/octocat/Hello-World/branches/master/protection/enforce_admins",
            "enabled": true
        },
        "required_pull_request_reviews": {
            "url": "https://api.github.com/repos/octocat/Hello-World/branches/master/protection/required_pull_request_reviews",
            "dismissal_restrictions": {
                "url": "https://api.github.com/repos/octocat/Hello-World/branches/master/protection/dismissal_restrictions",
                "users_url": "https://api.github.com/repos/octocat/Hello-World/branches/master/protection/dismissal_restrictions/users",
                "teams_url": "https://api.github.com/repos/octocat/Hello-World/branches/master/protection/dismissal_restrictions/teams",
                "users": [
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
                "teams": [
                    {
                        "id": 1,
                        "node_id": "MDQ6VGVhbTE=",
                        "url": "https://api.github.com/teams/1",
                        "html_url": "https://github.com/orgs/github/teams/justice-league",
                        "name": "Justice League",
                        "slug": "justice-league",
                        "description": "A great team.",
                        "privacy": "closed",
                        "notification_setting": "notifications_enabled",
                        "permission": "admin",
                        "members_url": "https://api.github.com/teams/1/members{/member}",
                        "repositories_url": "https://api.github.com/teams/1/repos",
                        "parent": null
                    }
                ],
                "apps": [
                    {
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
                            "hooks_url": "https://api.github.com/orgs/github/hooks",
                            "issues_url": "https://api.github.com/orgs/github/issues",
                            "members_url": "https://api.github.com/orgs/github/members{/member}",
                            "public_members_url": "https://api.github.com/orgs/github/public_members{/member}",
                            "avatar_url": "https://github.com/images/error/octocat_happy.gif",
                            "description": "A great organization"
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
                    }
                ]
            },
            "dismiss_stale_reviews": true,
            "require_code_owner_reviews": true,
            "required_approving_review_count": 2,
            "require_last_push_approval": true
        },
        "restrictions": {
            "url": "https://api.github.com/repos/octocat/Hello-World/branches/master/protection/restrictions",
            "users_url": "https://api.github.com/repos/octocat/Hello-World/branches/master/protection/restrictions/users",
            "teams_url": "https://api.github.com/repos/octocat/Hello-World/branches/master/protection/restrictions/teams",
            "apps_url": "https://api.github.com/repos/octocat/Hello-World/branches/master/protection/restrictions/apps",
            "users": [
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
            "teams": [
                {
                    "id": 1,
                    "node_id": "MDQ6VGVhbTE=",
                    "url": "https://api.github.com/teams/1",
                    "html_url": "https://github.com/orgs/github/teams/justice-league",
                    "name": "Justice League",
                    "slug": "justice-league",
                    "description": "A great team.",
                    "privacy": "closed",
                    "notification_setting": "notifications_enabled",
                    "permission": "admin",
                    "members_url": "https://api.github.com/teams/1/members{/member}",
                    "repositories_url": "https://api.github.com/teams/1/repos",
                    "parent": null
                }
            ],
            "apps": [
                {
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
                        "hooks_url": "https://api.github.com/orgs/github/hooks",
                        "issues_url": "https://api.github.com/orgs/github/issues",
                        "members_url": "https://api.github.com/orgs/github/members{/member}",
                        "public_members_url": "https://api.github.com/orgs/github/public_members{/member}",
                        "avatar_url": "https://github.com/images/error/octocat_happy.gif",
                        "description": "A great organization"
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
                }
            ]
        },
        "required_linear_history": {
            "enabled": true
        },
        "allow_force_pushes": {
            "enabled": true
        },
        "allow_deletions": {
            "enabled": true
        },
        "required_conversation_resolution": {
            "enabled": true
        },
        "lock_branch": {
            "enabled": true
        },
        "allow_fork_syncing": {
            "enabled": true
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