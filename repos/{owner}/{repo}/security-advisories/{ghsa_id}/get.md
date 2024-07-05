# Get a repository security advisory

Get a repository security advisory using its GitHub Security Advisory (GHSA) identifier.

Anyone can access any published security advisory on a public repository.

The authenticated user can access an unpublished security advisory from a repository if they are a security manager or administrator of that repository, or if they are a
collaborator on the security advisory.

OAuth app tokens and personal access tokens (classic) need the `repo` or `repository_advisories:read` scope to to get a published security advisory in a private repository, or any unpublished security advisory that the authenticated user has access to.

## Operation Object

```json
{
    "summary": "Get a repository security advisory",
    "description": "Get a repository security advisory using its GitHub Security Advisory (GHSA) identifier.\n\nAnyone can access any published security advisory on a public repository.\n\nThe authenticated user can access an unpublished security advisory from a repository if they are a security manager or administrator of that repository, or if they are a\ncollaborator on the security advisory.\n\nOAuth app tokens and personal access tokens (classic) need the `repo` or `repository_advisories:read` scope to to get a published security advisory in a private repository, or any unpublished security advisory that the authenticated user has access to.",
    "tags": [
        "security-advisories"
    ],
    "operationId": "security-advisories/get-repository-advisory",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/security-advisories/repository-advisories#get-a-repository-security-advisory"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "$ref": "#/components/parameters/ghsa_id"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/repository-advisory"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/repository-advisory"
                        }
                    }
                }
            }
        },
        "403": {
            "$ref": "#/components/responses/forbidden"
        },
        "404": {
            "$ref": "#/components/responses/not_found"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "security-advisories",
        "subcategory": "repository-advisories"
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

### `#/components/parameters/ghsa_id`

```json
{
    "name": "ghsa_id",
    "description": "The GHSA (GitHub Security Advisory) identifier of the advisory.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "string"
    }
}
```

### `#/components/schemas/repository-advisory`

```json
{
    "description": "A repository security advisory.",
    "type": "object",
    "properties": {
        "ghsa_id": {
            "type": "string",
            "description": "The GitHub Security Advisory ID.",
            "readOnly": true
        },
        "cve_id": {
            "type": "string",
            "description": "The Common Vulnerabilities and Exposures (CVE) ID.",
            "nullable": true
        },
        "url": {
            "type": "string",
            "format": "uri",
            "description": "The API URL for the advisory.",
            "readOnly": true
        },
        "html_url": {
            "type": "string",
            "format": "uri",
            "description": "The URL for the advisory.",
            "readOnly": true
        },
        "summary": {
            "type": "string",
            "description": "A short summary of the advisory.",
            "maxLength": 1024
        },
        "description": {
            "type": "string",
            "description": "A detailed description of what the advisory entails.",
            "maxLength": 65535,
            "nullable": true
        },
        "severity": {
            "type": "string",
            "description": "The severity of the advisory.",
            "nullable": true,
            "enum": [
                "critical",
                "high",
                "medium",
                "low"
            ]
        },
        "author": {
            "readOnly": true,
            "nullable": true,
            "description": "The author of the advisory.",
            "allOf": [
                {
                    "$ref": "#/components/schemas/simple-user"
                }
            ]
        },
        "publisher": {
            "readOnly": true,
            "nullable": true,
            "description": "The publisher of the advisory.",
            "allOf": [
                {
                    "$ref": "#/components/schemas/simple-user"
                }
            ]
        },
        "identifiers": {
            "type": "array",
            "items": {
                "type": "object",
                "properties": {
                    "type": {
                        "type": "string",
                        "description": "The type of identifier.",
                        "enum": [
                            "CVE",
                            "GHSA"
                        ]
                    },
                    "value": {
                        "type": "string",
                        "description": "The identifier value."
                    }
                },
                "required": [
                    "type",
                    "value"
                ]
            },
            "readOnly": true
        },
        "state": {
            "type": "string",
            "description": "The state of the advisory.",
            "enum": [
                "published",
                "closed",
                "withdrawn",
                "draft",
                "triage"
            ]
        },
        "created_at": {
            "type": "string",
            "format": "date-time",
            "description": "The date and time of when the advisory was created, in ISO 8601 format.",
            "readOnly": true,
            "nullable": true
        },
        "updated_at": {
            "type": "string",
            "format": "date-time",
            "description": "The date and time of when the advisory was last updated, in ISO 8601 format.",
            "readOnly": true,
            "nullable": true
        },
        "published_at": {
            "type": "string",
            "format": "date-time",
            "description": "The date and time of when the advisory was published, in ISO 8601 format.",
            "readOnly": true,
            "nullable": true
        },
        "closed_at": {
            "type": "string",
            "format": "date-time",
            "description": "The date and time of when the advisory was closed, in ISO 8601 format.",
            "readOnly": true,
            "nullable": true
        },
        "withdrawn_at": {
            "type": "string",
            "format": "date-time",
            "description": "The date and time of when the advisory was withdrawn, in ISO 8601 format.",
            "readOnly": true,
            "nullable": true
        },
        "submission": {
            "type": "object",
            "nullable": true,
            "readOnly": true,
            "properties": {
                "accepted": {
                    "type": "boolean",
                    "description": "Whether a private vulnerability report was accepted by the repository's administrators.",
                    "readOnly": true
                }
            },
            "required": [
                "accepted"
            ]
        },
        "vulnerabilities": {
            "type": "array",
            "nullable": true,
            "items": {
                "$ref": "#/components/schemas/repository-advisory-vulnerability"
            }
        },
        "cvss": {
            "type": "object",
            "nullable": true,
            "properties": {
                "vector_string": {
                    "type": "string",
                    "description": "The CVSS vector.",
                    "nullable": true
                },
                "score": {
                    "type": "number",
                    "description": "The CVSS score.",
                    "minimum": 0,
                    "maximum": 10,
                    "nullable": true,
                    "readOnly": true
                }
            },
            "required": [
                "vector_string",
                "score"
            ]
        },
        "cwes": {
            "type": "array",
            "nullable": true,
            "items": {
                "type": "object",
                "properties": {
                    "cwe_id": {
                        "type": "string",
                        "description": "The Common Weakness Enumeration (CWE) identifier."
                    },
                    "name": {
                        "type": "string",
                        "description": "The name of the CWE.",
                        "readOnly": true
                    }
                },
                "required": [
                    "cwe_id",
                    "name"
                ]
            },
            "readOnly": true
        },
        "cwe_ids": {
            "type": "array",
            "description": "A list of only the CWE IDs.",
            "nullable": true,
            "items": {
                "type": "string"
            }
        },
        "credits": {
            "type": "array",
            "nullable": true,
            "items": {
                "type": "object",
                "properties": {
                    "login": {
                        "type": "string",
                        "description": "The username of the user credited."
                    },
                    "type": {
                        "$ref": "#/components/schemas/security-advisory-credit-types"
                    }
                }
            }
        },
        "credits_detailed": {
            "type": "array",
            "nullable": true,
            "items": {
                "$ref": "#/components/schemas/repository-advisory-credit"
            },
            "readOnly": true
        },
        "collaborating_users": {
            "type": "array",
            "description": "A list of users that collaborate on the advisory.",
            "nullable": true,
            "items": {
                "$ref": "#/components/schemas/simple-user"
            }
        },
        "collaborating_teams": {
            "type": "array",
            "description": "A list of teams that collaborate on the advisory.",
            "nullable": true,
            "items": {
                "$ref": "#/components/schemas/team"
            }
        },
        "private_fork": {
            "readOnly": true,
            "nullable": true,
            "description": "A temporary private fork of the advisory's repository for collaborating on a fix.",
            "allOf": [
                {
                    "$ref": "#/components/schemas/simple-repository"
                }
            ]
        }
    },
    "required": [
        "ghsa_id",
        "cve_id",
        "url",
        "html_url",
        "summary",
        "description",
        "severity",
        "author",
        "publisher",
        "identifiers",
        "state",
        "created_at",
        "updated_at",
        "published_at",
        "closed_at",
        "withdrawn_at",
        "submission",
        "vulnerabilities",
        "cvss",
        "cwes",
        "cwe_ids",
        "credits",
        "credits_detailed",
        "collaborating_users",
        "collaborating_teams",
        "private_fork"
    ],
    "additionalProperties": false
}
```

### `#/components/examples/repository-advisory`

```json
{
    "value": {
        "ghsa_id": "GHSA-abcd-1234-efgh",
        "cve_id": "CVE-2050-00000",
        "url": "https://api.github.com/repos/repo/a-package/security-advisories/GHSA-abcd-1234-efgh",
        "html_url": "https://github.com/repo/a-package/security/advisories/GHSA-abcd-1234-efgh",
        "summary": "A short summary of the advisory.",
        "description": "A detailed description of what the advisory entails.",
        "severity": "critical",
        "author": {
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
        "publisher": {
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
        "identifiers": [
            {
                "type": "GHSA",
                "value": "GHSA-abcd-1234-efgh"
            },
            {
                "type": "CVE",
                "value": "CVE-2050-00000"
            }
        ],
        "state": "published",
        "created_at": "2020-01-01T00:00:00Z",
        "updated_at": "2020-01-02T00:00:00Z",
        "published_at": "2020-01-03T00:00:00Z",
        "closed_at": null,
        "withdrawn_at": null,
        "submission": null,
        "vulnerabilities": [
            {
                "package": {
                    "ecosystem": "pip",
                    "name": "a-package"
                },
                "vulnerable_version_range": ">= 1.0.0, < 1.0.1",
                "patched_versions": "1.0.1",
                "vulnerable_functions": [
                    "function1"
                ]
            },
            {
                "package": {
                    "ecosystem": "pip",
                    "name": "another-package"
                },
                "vulnerable_version_range": ">= 1.0.0, < 1.0.2",
                "patched_versions": "1.0.2",
                "vulnerable_functions": [
                    "function2"
                ]
            }
        ],
        "cvss": {
            "vector_string": "CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:H",
            "score": 9.8
        },
        "cwes": [
            {
                "cwe_id": "CWE-123",
                "name": "A CWE"
            }
        ],
        "cwe_ids": [
            "CWE-123"
        ],
        "credits": [
            {
                "login": "octocat",
                "type": "analyst"
            }
        ],
        "credits_detailed": [
            {
                "user": {
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
                "type": "analyst",
                "state": "accepted"
            }
        ],
        "collaborating_users": [
            {
                "login": "octokitten",
                "id": 1,
                "node_id": "MDQ6VXNlcjE=",
                "avatar_url": "https://github.com/images/error/octokitten_happy.gif",
                "gravatar_id": "",
                "url": "https://api.github.com/users/octokitten",
                "html_url": "https://github.com/octokitten",
                "followers_url": "https://api.github.com/users/octokitten/followers",
                "following_url": "https://api.github.com/users/octokitten/following{/other_user}",
                "gists_url": "https://api.github.com/users/octokitten/gists{/gist_id}",
                "starred_url": "https://api.github.com/users/octokitten/starred{/owner}{/repo}",
                "subscriptions_url": "https://api.github.com/users/octokitten/subscriptions",
                "organizations_url": "https://api.github.com/users/octokitten/orgs",
                "repos_url": "https://api.github.com/users/octokitten/repos",
                "events_url": "https://api.github.com/users/octokitten/events{/privacy}",
                "received_events_url": "https://api.github.com/users/octokitten/received_events",
                "type": "User",
                "site_admin": false
            }
        ],
        "collaborating_teams": [
            {
                "name": "Justice League",
                "id": 1,
                "node_id": "MDQ6VGVhbTE=",
                "slug": "justice-league",
                "description": "A great team.",
                "privacy": "closed",
                "notification_setting": "notifications_enabled",
                "url": "https://api.github.com/teams/1",
                "html_url": "https://github.com/orgs/github/teams/justice-league",
                "members_url": "https://api.github.com/teams/1/members{/member}",
                "repositories_url": "https://api.github.com/teams/1/repos",
                "permission": "admin",
                "parent": null
            }
        ],
        "private_fork": {
            "id": 217723378,
            "node_id": "MDEwOlJlcG9zaXRvcnkyMTc3MjMzNzg=",
            "name": "octo-repo-ghsa-abcd-1234-efgh",
            "full_name": "octo-org/octo-repo-ghsa-abcd-1234-efgh",
            "owner": {
                "login": "octo-org",
                "id": 6811672,
                "node_id": "MDEyOk9yZ2FuaXphdGlvbjY4MTE2NzI=",
                "avatar_url": "https://avatars3.githubusercontent.com/u/6811672?v=4",
                "gravatar_id": "",
                "url": "https://api.github.com/users/octo-org",
                "html_url": "https://github.com/octo-org",
                "followers_url": "https://api.github.com/users/octo-org/followers",
                "following_url": "https://api.github.com/users/octo-org/following{/other_user}",
                "gists_url": "https://api.github.com/users/octo-org/gists{/gist_id}",
                "starred_url": "https://api.github.com/users/octo-org/starred{/owner}{/repo}",
                "subscriptions_url": "https://api.github.com/users/octo-org/subscriptions",
                "organizations_url": "https://api.github.com/users/octo-org/orgs",
                "repos_url": "https://api.github.com/users/octo-org/repos",
                "events_url": "https://api.github.com/users/octo-org/events{/privacy}",
                "received_events_url": "https://api.github.com/users/octo-org/received_events",
                "type": "Organization",
                "site_admin": false
            },
            "private": true,
            "html_url": "https://github.com/octo-org/octo-repo-ghsa-abcd-1234-efgh",
            "description": null,
            "fork": false,
            "url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-abcd-1234-efgh",
            "archive_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-abcd-1234-efgh/{archive_format}{/ref}",
            "assignees_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-abcd-1234-efgh/assignees{/user}",
            "blobs_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-abcd-1234-efgh/git/blobs{/sha}",
            "branches_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-abcd-1234-efgh/branches{/branch}",
            "collaborators_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-abcd-1234-efgh/collaborators{/collaborator}",
            "comments_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-abcd-1234-efgh/comments{/number}",
            "commits_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-abcd-1234-efgh/commits{/sha}",
            "compare_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-abcd-1234-efgh/compare/{base}...{head}",
            "contents_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-abcd-1234-efgh/contents/{+path}",
            "contributors_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-abcd-1234-efgh/contributors",
            "deployments_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-abcd-1234-efgh/deployments",
            "downloads_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-abcd-1234-efgh/downloads",
            "events_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-abcd-1234-efgh/events",
            "forks_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-abcd-1234-efgh/forks",
            "git_commits_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-abcd-1234-efgh/git/commits{/sha}",
            "git_refs_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-abcd-1234-efgh/git/refs{/sha}",
            "git_tags_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-abcd-1234-efgh/git/tags{/sha}",
            "hooks_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-abcd-1234-efgh/hooks",
            "issue_comment_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-abcd-1234-efgh/issues/comments{/number}",
            "issue_events_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-abcd-1234-efgh/issues/events{/number}",
            "issues_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-abcd-1234-efgh/issues{/number}",
            "keys_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-abcd-1234-efgh/keys{/key_id}",
            "labels_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-abcd-1234-efgh/labels{/name}",
            "languages_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-abcd-1234-efgh/languages",
            "merges_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-abcd-1234-efgh/merges",
            "milestones_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-abcd-1234-efgh/milestones{/number}",
            "notifications_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-abcd-1234-efgh/notifications{?since,all,participating}",
            "pulls_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-abcd-1234-efgh/pulls{/number}",
            "releases_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-abcd-1234-efgh/releases{/id}",
            "stargazers_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-abcd-1234-efgh/stargazers",
            "statuses_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-abcd-1234-efgh/statuses/{sha}",
            "subscribers_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-abcd-1234-efgh/subscribers",
            "subscription_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-abcd-1234-efgh/subscription",
            "tags_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-abcd-1234-efgh/tags",
            "teams_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-abcd-1234-efgh/teams",
            "trees_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-abcd-1234-efgh/git/trees{/sha}"
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