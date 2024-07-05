# List repository security advisories

Lists security advisories in a repository.

The authenticated user can access unpublished security advisories from a repository if they are a security manager or administrator of that repository, or if they are a collaborator on any security advisory.

OAuth app tokens and personal access tokens (classic) need the `repo` or `repository_advisories:read` scope to to get a published security advisory in a private repository, or any unpublished security advisory that the authenticated user has access to.

## Operation Object

```json
{
    "summary": "List repository security advisories",
    "description": "Lists security advisories in a repository.\n\nThe authenticated user can access unpublished security advisories from a repository if they are a security manager or administrator of that repository, or if they are a collaborator on any security advisory.\n\nOAuth app tokens and personal access tokens (classic) need the `repo` or `repository_advisories:read` scope to to get a published security advisory in a private repository, or any unpublished security advisory that the authenticated user has access to.",
    "tags": [
        "security-advisories"
    ],
    "operationId": "security-advisories/list-repository-advisories",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/security-advisories/repository-advisories#list-repository-security-advisories"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "$ref": "#/components/parameters/direction"
        },
        {
            "name": "sort",
            "description": "The property to sort the results by.",
            "in": "query",
            "required": false,
            "schema": {
                "type": "string",
                "enum": [
                    "created",
                    "updated",
                    "published"
                ],
                "default": "created"
            }
        },
        {
            "$ref": "#/components/parameters/pagination-before"
        },
        {
            "$ref": "#/components/parameters/pagination-after"
        },
        {
            "name": "per_page",
            "description": "The number of advisories to return per page. For more information, see \"[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api).\"",
            "in": "query",
            "required": false,
            "schema": {
                "type": "integer",
                "minimum": 1,
                "maximum": 100,
                "default": 30
            }
        },
        {
            "name": "state",
            "description": "Filter by state of the repository advisories. Only advisories of this state will be returned.",
            "in": "query",
            "required": false,
            "schema": {
                "type": "string",
                "enum": [
                    "triage",
                    "draft",
                    "published",
                    "closed"
                ]
            }
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "type": "array",
                        "items": {
                            "$ref": "#/components/schemas/repository-advisory"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/list-repository-advisories"
                        }
                    }
                }
            }
        },
        "400": {
            "$ref": "#/components/responses/bad_request"
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

### `#/components/parameters/direction`

```json
{
    "name": "direction",
    "description": "The direction to sort the results by.",
    "in": "query",
    "required": false,
    "schema": {
        "type": "string",
        "enum": [
            "asc",
            "desc"
        ],
        "default": "desc"
    }
}
```

### `#/components/parameters/pagination-before`

```json
{
    "name": "before",
    "description": "A cursor, as given in the [Link header](https://docs.github.com/rest/guides/using-pagination-in-the-rest-api#using-link-headers). If specified, the query only searches for results before this cursor. For more information, see \"[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api).\"",
    "in": "query",
    "required": false,
    "schema": {
        "type": "string"
    }
}
```

### `#/components/parameters/pagination-after`

```json
{
    "name": "after",
    "description": "A cursor, as given in the [Link header](https://docs.github.com/rest/guides/using-pagination-in-the-rest-api#using-link-headers). If specified, the query only searches for results after this cursor. For more information, see \"[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api).\"",
    "in": "query",
    "required": false,
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

### `#/components/examples/list-repository-advisories`

```json
{
    "value": [
        {
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
            "private_fork": null
        },
        {
            "ghsa_id": "GHSA-1234-5678-9012",
            "cve_id": "CVE-2051-0000",
            "url": "https://api.github.com/repos/repo/a-package/security-advisories/GHSA-1234-5678-9012",
            "html_url": "https://github.com/repo/a-package/security/advisories/GHSA-1234-5678-9012",
            "summary": "A short summary of the advisory.",
            "description": "A detailed description of what the advisory entails.",
            "severity": "low",
            "author": {
                "login": "monauser",
                "id": 2,
                "node_id": "MDQ6VXNlcjE=",
                "avatar_url": "https://github.com/images/error/octocat_happy.gif",
                "gravatar_id": "",
                "url": "https://api.github.com/users/monauser",
                "html_url": "https://github.com/monauser",
                "followers_url": "https://api.github.com/users/monauser/followers",
                "following_url": "https://api.github.com/users/monauser/following{/other_user}",
                "gists_url": "https://api.github.com/users/monauser/gists{/gist_id}",
                "starred_url": "https://api.github.com/users/monauser/starred{/owner}{/repo}",
                "subscriptions_url": "https://api.github.com/users/monauser/subscriptions",
                "organizations_url": "https://api.github.com/users/monauser/orgs",
                "repos_url": "https://api.github.com/users/monauser/repos",
                "events_url": "https://api.github.com/users/monauser/events{/privacy}",
                "received_events_url": "https://api.github.com/users/monauser/received_events",
                "type": "User",
                "site_admin": false
            },
            "publisher": {
                "login": "monalisa",
                "id": 3,
                "node_id": "MDQ6VXNlcjE=",
                "avatar_url": "https://github.com/images/error/octocat_happy.gif",
                "gravatar_id": "",
                "url": "https://api.github.com/users/monalisa",
                "html_url": "https://github.com/monalisa",
                "followers_url": "https://api.github.com/users/monalisa/followers",
                "following_url": "https://api.github.com/users/monalisa/following{/other_user}",
                "gists_url": "https://api.github.com/users/monalisa/gists{/gist_id}",
                "starred_url": "https://api.github.com/users/monalisa/starred{/owner}{/repo}",
                "subscriptions_url": "https://api.github.com/users/monalisa/subscriptions",
                "organizations_url": "https://api.github.com/users/monalisa/orgs",
                "repos_url": "https://api.github.com/users/monalisa/repos",
                "events_url": "https://api.github.com/users/monalisa/events{/privacy}",
                "received_events_url": "https://api.github.com/users/monalisa/received_events",
                "type": "User",
                "site_admin": false
            },
            "identifiers": [
                {
                    "type": "GHSA",
                    "value": "GHSA-1234-5678-9012"
                },
                {
                    "type": "CVE",
                    "value": "CVE-2051-00000"
                }
            ],
            "state": "published",
            "created_at": "2020-01-03T00:00:00Z",
            "updated_at": "2020-01-04T00:00:00Z",
            "published_at": "2020-01-04T00:00:00Z",
            "closed_at": null,
            "withdrawn_at": null,
            "submission": {
                "accepted": true
            },
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
                "vector_string": "AV:P/AC:H/PR:H/UI:R/S:U/C:N/I:L/A:N",
                "score": 1.6
            },
            "cwes": [
                {
                    "cwe_id": "CWE-456",
                    "name": "A CWE 2.0"
                }
            ],
            "cwe_ids": [
                "CWE-456"
            ],
            "credits": [
                {
                    "login": "monauser",
                    "type": "reporter"
                }
            ],
            "credits_detailed": [
                {
                    "user": {
                        "login": "monauser",
                        "id": 2,
                        "node_id": "MDQ6VXNlcjE=",
                        "avatar_url": "https://github.com/images/error/octocat_happy.gif",
                        "gravatar_id": "",
                        "url": "https://api.github.com/users/monauser",
                        "html_url": "https://github.com/monauser",
                        "followers_url": "https://api.github.com/users/monauser/followers",
                        "following_url": "https://api.github.com/users/monauser/following{/other_user}",
                        "gists_url": "https://api.github.com/users/monauser/gists{/gist_id}",
                        "starred_url": "https://api.github.com/users/monauser/starred{/owner}{/repo}",
                        "subscriptions_url": "https://api.github.com/users/monauser/subscriptions",
                        "organizations_url": "https://api.github.com/users/monauser/orgs",
                        "repos_url": "https://api.github.com/users/monauser/repos",
                        "events_url": "https://api.github.com/users/monauser/events{/privacy}",
                        "received_events_url": "https://api.github.com/users/monauser/received_events",
                        "type": "User",
                        "site_admin": false
                    },
                    "type": "reporter",
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
                "name": "octo-repo-ghsa-1234-5678-9012",
                "full_name": "octo-org/octo-repo-ghsa-1234-5678-9012",
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
                "html_url": "https://github.com/octo-org/octo-repo-ghsa-1234-5678-9012",
                "description": null,
                "fork": false,
                "url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-1234-5678-9012",
                "archive_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-1234-5678-9012/{archive_format}{/ref}",
                "assignees_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-1234-5678-9012/assignees{/user}",
                "blobs_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-1234-5678-9012/git/blobs{/sha}",
                "branches_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-1234-5678-9012/branches{/branch}",
                "collaborators_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-1234-5678-9012/collaborators{/collaborator}",
                "comments_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-1234-5678-9012/comments{/number}",
                "commits_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-1234-5678-9012/commits{/sha}",
                "compare_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-1234-5678-9012/compare/{base}...{head}",
                "contents_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-1234-5678-9012/contents/{+path}",
                "contributors_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-1234-5678-9012/contributors",
                "deployments_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-1234-5678-9012/deployments",
                "downloads_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-1234-5678-9012/downloads",
                "events_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-1234-5678-9012/events",
                "forks_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-1234-5678-9012/forks",
                "git_commits_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-1234-5678-9012/git/commits{/sha}",
                "git_refs_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-1234-5678-9012/git/refs{/sha}",
                "git_tags_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-1234-5678-9012/git/tags{/sha}",
                "hooks_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-1234-5678-9012/hooks",
                "issue_comment_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-1234-5678-9012/issues/comments{/number}",
                "issue_events_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-1234-5678-9012/issues/events{/number}",
                "issues_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-1234-5678-9012/issues{/number}",
                "keys_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-1234-5678-9012/keys{/key_id}",
                "labels_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-1234-5678-9012/labels{/name}",
                "languages_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-1234-5678-9012/languages",
                "merges_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-1234-5678-9012/merges",
                "milestones_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-1234-5678-9012/milestones{/number}",
                "notifications_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-1234-5678-9012/notifications{?since,all,participating}",
                "pulls_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-1234-5678-9012/pulls{/number}",
                "releases_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-1234-5678-9012/releases{/id}",
                "stargazers_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-1234-5678-9012/stargazers",
                "statuses_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-1234-5678-9012/statuses/{sha}",
                "subscribers_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-1234-5678-9012/subscribers",
                "subscription_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-1234-5678-9012/subscription",
                "tags_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-1234-5678-9012/tags",
                "teams_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-1234-5678-9012/teams",
                "trees_url": "https://api.github.com/repos/octo-org/octo-repo-ghsa-1234-5678-9012/git/trees{/sha}"
            }
        }
    ]
}
```

### `#/components/responses/bad_request`

```json
{
    "description": "Bad Request",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/basic-error"
            }
        },
        "application/scim+json": {
            "schema": {
                "$ref": "#/components/schemas/scim-error"
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