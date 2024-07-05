# Get access restrictions

`get /repos/{owner}/{repo}/branches/{branch}/protection/restrictions`

Protected branches are available in public repositories with GitHub Free and GitHub Free for organizations, and in public and private repositories with GitHub Pro, GitHub Team, GitHub Enterprise Cloud, and GitHub Enterprise Server. For more information, see [GitHub's products](https://docs.github.com/github/getting-started-with-github/githubs-products) in the GitHub Help documentation.

Lists who has access to this protected branch.

**Note**: Users, apps, and teams `restrictions` are only available for organization-owned repositories.

## Operation Object

```json
{
    "summary": "Get access restrictions",
    "description": "Protected branches are available in public repositories with GitHub Free and GitHub Free for organizations, and in public and private repositories with GitHub Pro, GitHub Team, GitHub Enterprise Cloud, and GitHub Enterprise Server. For more information, see [GitHub's products](https://docs.github.com/github/getting-started-with-github/githubs-products) in the GitHub Help documentation.\n\nLists who has access to this protected branch.\n\n**Note**: Users, apps, and teams `restrictions` are only available for organization-owned repositories.",
    "tags": [
        "repos"
    ],
    "operationId": "repos/get-access-restrictions",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/branches/branch-protection#get-access-restrictions"
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
                        "$ref": "#/components/schemas/branch-restriction-policy"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/branch-restriction-policy"
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

### `#/components/schemas/branch-restriction-policy`

```json
{
    "title": "Branch Restriction Policy",
    "description": "Branch Restriction Policy",
    "type": "object",
    "properties": {
        "url": {
            "type": "string",
            "format": "uri"
        },
        "users_url": {
            "type": "string",
            "format": "uri"
        },
        "teams_url": {
            "type": "string",
            "format": "uri"
        },
        "apps_url": {
            "type": "string",
            "format": "uri"
        },
        "users": {
            "type": "array",
            "items": {
                "type": "object",
                "properties": {
                    "login": {
                        "type": "string"
                    },
                    "id": {
                        "type": "integer",
                        "format": "int64"
                    },
                    "node_id": {
                        "type": "string"
                    },
                    "avatar_url": {
                        "type": "string"
                    },
                    "gravatar_id": {
                        "type": "string"
                    },
                    "url": {
                        "type": "string"
                    },
                    "html_url": {
                        "type": "string"
                    },
                    "followers_url": {
                        "type": "string"
                    },
                    "following_url": {
                        "type": "string"
                    },
                    "gists_url": {
                        "type": "string"
                    },
                    "starred_url": {
                        "type": "string"
                    },
                    "subscriptions_url": {
                        "type": "string"
                    },
                    "organizations_url": {
                        "type": "string"
                    },
                    "repos_url": {
                        "type": "string"
                    },
                    "events_url": {
                        "type": "string"
                    },
                    "received_events_url": {
                        "type": "string"
                    },
                    "type": {
                        "type": "string"
                    },
                    "site_admin": {
                        "type": "boolean"
                    }
                }
            }
        },
        "teams": {
            "type": "array",
            "items": {
                "type": "object",
                "properties": {
                    "id": {
                        "type": "integer"
                    },
                    "node_id": {
                        "type": "string"
                    },
                    "url": {
                        "type": "string"
                    },
                    "html_url": {
                        "type": "string"
                    },
                    "name": {
                        "type": "string"
                    },
                    "slug": {
                        "type": "string"
                    },
                    "description": {
                        "type": "string",
                        "nullable": true
                    },
                    "privacy": {
                        "type": "string"
                    },
                    "notification_setting": {
                        "type": "string"
                    },
                    "permission": {
                        "type": "string"
                    },
                    "members_url": {
                        "type": "string"
                    },
                    "repositories_url": {
                        "type": "string"
                    },
                    "parent": {
                        "type": "string",
                        "nullable": true
                    }
                }
            }
        },
        "apps": {
            "type": "array",
            "items": {
                "type": "object",
                "properties": {
                    "id": {
                        "type": "integer"
                    },
                    "slug": {
                        "type": "string"
                    },
                    "node_id": {
                        "type": "string"
                    },
                    "owner": {
                        "type": "object",
                        "properties": {
                            "login": {
                                "type": "string"
                            },
                            "id": {
                                "type": "integer"
                            },
                            "node_id": {
                                "type": "string"
                            },
                            "url": {
                                "type": "string"
                            },
                            "repos_url": {
                                "type": "string"
                            },
                            "events_url": {
                                "type": "string"
                            },
                            "hooks_url": {
                                "type": "string"
                            },
                            "issues_url": {
                                "type": "string"
                            },
                            "members_url": {
                                "type": "string"
                            },
                            "public_members_url": {
                                "type": "string"
                            },
                            "avatar_url": {
                                "type": "string"
                            },
                            "description": {
                                "type": "string"
                            },
                            "gravatar_id": {
                                "type": "string",
                                "example": "\"\""
                            },
                            "html_url": {
                                "type": "string",
                                "example": "\"https://github.com/testorg-ea8ec76d71c3af4b\""
                            },
                            "followers_url": {
                                "type": "string",
                                "example": "\"https://api.github.com/users/testorg-ea8ec76d71c3af4b/followers\""
                            },
                            "following_url": {
                                "type": "string",
                                "example": "\"https://api.github.com/users/testorg-ea8ec76d71c3af4b/following{/other_user}\""
                            },
                            "gists_url": {
                                "type": "string",
                                "example": "\"https://api.github.com/users/testorg-ea8ec76d71c3af4b/gists{/gist_id}\""
                            },
                            "starred_url": {
                                "type": "string",
                                "example": "\"https://api.github.com/users/testorg-ea8ec76d71c3af4b/starred{/owner}{/repo}\""
                            },
                            "subscriptions_url": {
                                "type": "string",
                                "example": "\"https://api.github.com/users/testorg-ea8ec76d71c3af4b/subscriptions\""
                            },
                            "organizations_url": {
                                "type": "string",
                                "example": "\"https://api.github.com/users/testorg-ea8ec76d71c3af4b/orgs\""
                            },
                            "received_events_url": {
                                "type": "string",
                                "example": "\"https://api.github.com/users/testorg-ea8ec76d71c3af4b/received_events\""
                            },
                            "type": {
                                "type": "string",
                                "example": "\"Organization\""
                            },
                            "site_admin": {
                                "type": "boolean",
                                "example": false
                            }
                        }
                    },
                    "name": {
                        "type": "string"
                    },
                    "description": {
                        "type": "string"
                    },
                    "external_url": {
                        "type": "string"
                    },
                    "html_url": {
                        "type": "string"
                    },
                    "created_at": {
                        "type": "string"
                    },
                    "updated_at": {
                        "type": "string"
                    },
                    "permissions": {
                        "type": "object",
                        "properties": {
                            "metadata": {
                                "type": "string"
                            },
                            "contents": {
                                "type": "string"
                            },
                            "issues": {
                                "type": "string"
                            },
                            "single_file": {
                                "type": "string"
                            }
                        }
                    },
                    "events": {
                        "type": "array",
                        "items": {
                            "type": "string"
                        }
                    }
                }
            }
        }
    },
    "required": [
        "url",
        "users_url",
        "teams_url",
        "apps_url",
        "users",
        "teams",
        "apps"
    ]
}
```

### `#/components/examples/branch-restriction-policy`

```json
{
    "value": {
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