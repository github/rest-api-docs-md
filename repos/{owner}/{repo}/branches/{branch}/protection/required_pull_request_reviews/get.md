# Get pull request review protection

`get /repos/{owner}/{repo}/branches/{branch}/protection/required_pull_request_reviews`

Protected branches are available in public repositories with GitHub Free and GitHub Free for organizations, and in public and private repositories with GitHub Pro, GitHub Team, GitHub Enterprise Cloud, and GitHub Enterprise Server. For more information, see [GitHub's products](https://docs.github.com/github/getting-started-with-github/githubs-products) in the GitHub Help documentation.

## Operation Object

```json
{
    "summary": "Get pull request review protection",
    "description": "Protected branches are available in public repositories with GitHub Free and GitHub Free for organizations, and in public and private repositories with GitHub Pro, GitHub Team, GitHub Enterprise Cloud, and GitHub Enterprise Server. For more information, see [GitHub's products](https://docs.github.com/github/getting-started-with-github/githubs-products) in the GitHub Help documentation.",
    "tags": [
        "repos"
    ],
    "operationId": "repos/get-pull-request-review-protection",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/branches/branch-protection#get-pull-request-review-protection"
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
                        "$ref": "#/components/schemas/protected-branch-pull-request-review"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/protected-branch-pull-request-review"
                        }
                    }
                }
            }
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

### `#/components/schemas/protected-branch-pull-request-review`

```json
{
    "title": "Protected Branch Pull Request Review",
    "description": "Protected Branch Pull Request Review",
    "type": "object",
    "properties": {
        "url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/repos/octocat/Hello-World/branches/master/protection/dismissal_restrictions"
        },
        "dismissal_restrictions": {
            "type": "object",
            "properties": {
                "users": {
                    "description": "The list of users with review dismissal access.",
                    "type": "array",
                    "items": {
                        "$ref": "#/components/schemas/simple-user"
                    }
                },
                "teams": {
                    "description": "The list of teams with review dismissal access.",
                    "type": "array",
                    "items": {
                        "$ref": "#/components/schemas/team"
                    }
                },
                "apps": {
                    "description": "The list of apps with review dismissal access.",
                    "type": "array",
                    "items": {
                        "$ref": "#/components/schemas/integration"
                    }
                },
                "url": {
                    "type": "string",
                    "example": "\"https://api.github.com/repos/the-org/an-org-repo/branches/master/protection/dismissal_restrictions\""
                },
                "users_url": {
                    "type": "string",
                    "example": "\"https://api.github.com/repos/the-org/an-org-repo/branches/master/protection/dismissal_restrictions/users\""
                },
                "teams_url": {
                    "type": "string",
                    "example": "\"https://api.github.com/repos/the-org/an-org-repo/branches/master/protection/dismissal_restrictions/teams\""
                }
            }
        },
        "bypass_pull_request_allowances": {
            "type": "object",
            "description": "Allow specific users, teams, or apps to bypass pull request requirements.",
            "properties": {
                "users": {
                    "description": "The list of users allowed to bypass pull request requirements.",
                    "type": "array",
                    "items": {
                        "$ref": "#/components/schemas/simple-user"
                    }
                },
                "teams": {
                    "description": "The list of teams allowed to bypass pull request requirements.",
                    "type": "array",
                    "items": {
                        "$ref": "#/components/schemas/team"
                    }
                },
                "apps": {
                    "description": "The list of apps allowed to bypass pull request requirements.",
                    "type": "array",
                    "items": {
                        "$ref": "#/components/schemas/integration"
                    }
                }
            }
        },
        "dismiss_stale_reviews": {
            "type": "boolean",
            "example": true
        },
        "require_code_owner_reviews": {
            "type": "boolean",
            "example": true
        },
        "required_approving_review_count": {
            "type": "integer",
            "minimum": 0,
            "maximum": 6,
            "example": 2
        },
        "require_last_push_approval": {
            "description": "Whether the most recent push must be approved by someone other than the person who pushed it.",
            "type": "boolean",
            "example": true,
            "default": false
        }
    },
    "required": [
        "dismiss_stale_reviews",
        "require_code_owner_reviews"
    ]
}
```

### `#/components/examples/protected-branch-pull-request-review`

```json
{
    "value": {
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
    }
}
```