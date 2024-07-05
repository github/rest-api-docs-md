# List Dependabot alerts for a repository

`get /repos/{owner}/{repo}/dependabot/alerts`

OAuth app tokens and personal access tokens (classic) need the `security_events` scope to use this endpoint. If this endpoint is only used with public repositories, the token can use the `public_repo` scope instead.

## Operation Object

```json
{
    "summary": "List Dependabot alerts for a repository",
    "description": "OAuth app tokens and personal access tokens (classic) need the `security_events` scope to use this endpoint. If this endpoint is only used with public repositories, the token can use the `public_repo` scope instead.",
    "tags": [
        "dependabot"
    ],
    "operationId": "dependabot/list-alerts-for-repo",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/dependabot/alerts#list-dependabot-alerts-for-a-repository"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "$ref": "#/components/parameters/dependabot-alert-comma-separated-states"
        },
        {
            "$ref": "#/components/parameters/dependabot-alert-comma-separated-severities"
        },
        {
            "$ref": "#/components/parameters/dependabot-alert-comma-separated-ecosystems"
        },
        {
            "$ref": "#/components/parameters/dependabot-alert-comma-separated-packages"
        },
        {
            "$ref": "#/components/parameters/dependabot-alert-comma-separated-manifests"
        },
        {
            "$ref": "#/components/parameters/dependabot-alert-scope"
        },
        {
            "$ref": "#/components/parameters/dependabot-alert-sort"
        },
        {
            "$ref": "#/components/parameters/direction"
        },
        {
            "name": "page",
            "description": "**Deprecated**. Page number of the results to fetch. Use cursor-based pagination with `before` or `after` instead.",
            "deprecated": true,
            "in": "query",
            "schema": {
                "type": "integer",
                "default": 1
            }
        },
        {
            "name": "per_page",
            "description": "The number of results per page (max 100). For more information, see \"[Using pagination in the REST API](https://docs.github.com/rest/using-the-rest-api/using-pagination-in-the-rest-api).\"",
            "deprecated": true,
            "in": "query",
            "schema": {
                "type": "integer",
                "default": 30
            }
        },
        {
            "$ref": "#/components/parameters/pagination-before"
        },
        {
            "$ref": "#/components/parameters/pagination-after"
        },
        {
            "$ref": "#/components/parameters/pagination-first"
        },
        {
            "$ref": "#/components/parameters/pagination-last"
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
                            "$ref": "#/components/schemas/dependabot-alert"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/dependabot-alerts-for-repository"
                        }
                    }
                }
            }
        },
        "304": {
            "$ref": "#/components/responses/not_modified"
        },
        "400": {
            "$ref": "#/components/responses/bad_request"
        },
        "403": {
            "$ref": "#/components/responses/forbidden"
        },
        "404": {
            "$ref": "#/components/responses/not_found"
        },
        "422": {
            "$ref": "#/components/responses/validation_failed_simple"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "previews": [],
        "category": "dependabot",
        "subcategory": "alerts"
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

### `#/components/parameters/dependabot-alert-comma-separated-states`

```json
{
    "name": "state",
    "in": "query",
    "description": "A comma-separated list of states. If specified, only alerts with these states will be returned.\n\nCan be: `auto_dismissed`, `dismissed`, `fixed`, `open`",
    "schema": {
        "type": "string"
    }
}
```

### `#/components/parameters/dependabot-alert-comma-separated-severities`

```json
{
    "name": "severity",
    "in": "query",
    "description": "A comma-separated list of severities. If specified, only alerts with these severities will be returned.\n\nCan be: `low`, `medium`, `high`, `critical`",
    "schema": {
        "type": "string"
    }
}
```

### `#/components/parameters/dependabot-alert-comma-separated-ecosystems`

```json
{
    "name": "ecosystem",
    "in": "query",
    "description": "A comma-separated list of ecosystems. If specified, only alerts for these ecosystems will be returned.\n\nCan be: `composer`, `go`, `maven`, `npm`, `nuget`, `pip`, `pub`, `rubygems`, `rust`",
    "schema": {
        "type": "string"
    }
}
```

### `#/components/parameters/dependabot-alert-comma-separated-packages`

```json
{
    "name": "package",
    "in": "query",
    "description": "A comma-separated list of package names. If specified, only alerts for these packages will be returned.",
    "schema": {
        "type": "string"
    }
}
```

### `#/components/parameters/dependabot-alert-comma-separated-manifests`

```json
{
    "name": "manifest",
    "in": "query",
    "description": "A comma-separated list of full manifest paths. If specified, only alerts for these manifests will be returned.",
    "schema": {
        "type": "string"
    }
}
```

### `#/components/parameters/dependabot-alert-scope`

```json
{
    "name": "scope",
    "in": "query",
    "description": "The scope of the vulnerable dependency. If specified, only alerts with this scope will be returned.",
    "schema": {
        "type": "string",
        "enum": [
            "development",
            "runtime"
        ]
    }
}
```

### `#/components/parameters/dependabot-alert-sort`

```json
{
    "name": "sort",
    "in": "query",
    "description": "The property by which to sort the results.\n`created` means when the alert was created.\n`updated` means when the alert's state last changed.",
    "schema": {
        "type": "string",
        "enum": [
            "created",
            "updated"
        ],
        "default": "created"
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

### `#/components/parameters/pagination-first`

```json
{
    "name": "first",
    "description": "**Deprecated**. The number of results per page (max 100), starting from the first matching result.\nThis parameter must not be used in combination with `last`.\nInstead, use `per_page` in combination with `after` to fetch the first page of results.",
    "in": "query",
    "required": false,
    "schema": {
        "type": "integer",
        "minimum": 1,
        "maximum": 100,
        "default": 30
    }
}
```

### `#/components/parameters/pagination-last`

```json
{
    "name": "last",
    "description": "**Deprecated**. The number of results per page (max 100), starting from the last matching result.\nThis parameter must not be used in combination with `first`.\nInstead, use `per_page` in combination with `before` to fetch the last page of results.",
    "in": "query",
    "required": false,
    "schema": {
        "type": "integer",
        "minimum": 1,
        "maximum": 100
    }
}
```

### `#/components/schemas/dependabot-alert`

```json
{
    "type": "object",
    "description": "A Dependabot alert.",
    "properties": {
        "number": {
            "$ref": "#/components/schemas/alert-number"
        },
        "state": {
            "type": "string",
            "description": "The state of the Dependabot alert.",
            "readOnly": true,
            "enum": [
                "auto_dismissed",
                "dismissed",
                "fixed",
                "open"
            ]
        },
        "dependency": {
            "type": "object",
            "description": "Details for the vulnerable dependency.",
            "readOnly": true,
            "properties": {
                "package": {
                    "$ref": "#/components/schemas/dependabot-alert-package"
                },
                "manifest_path": {
                    "type": "string",
                    "description": "The full path to the dependency manifest file, relative to the root of the repository.",
                    "readOnly": true
                },
                "scope": {
                    "type": "string",
                    "description": "The execution scope of the vulnerable dependency.",
                    "readOnly": true,
                    "nullable": true,
                    "enum": [
                        "development",
                        "runtime"
                    ]
                }
            }
        },
        "security_advisory": {
            "$ref": "#/components/schemas/dependabot-alert-security-advisory"
        },
        "security_vulnerability": {
            "$ref": "#/components/schemas/dependabot-alert-security-vulnerability"
        },
        "url": {
            "$ref": "#/components/schemas/alert-url"
        },
        "html_url": {
            "$ref": "#/components/schemas/alert-html-url"
        },
        "created_at": {
            "$ref": "#/components/schemas/alert-created-at"
        },
        "updated_at": {
            "$ref": "#/components/schemas/alert-updated-at"
        },
        "dismissed_at": {
            "$ref": "#/components/schemas/alert-dismissed-at"
        },
        "dismissed_by": {
            "$ref": "#/components/schemas/nullable-simple-user"
        },
        "dismissed_reason": {
            "type": "string",
            "description": "The reason that the alert was dismissed.",
            "nullable": true,
            "enum": [
                "fix_started",
                "inaccurate",
                "no_bandwidth",
                "not_used",
                "tolerable_risk"
            ]
        },
        "dismissed_comment": {
            "type": "string",
            "description": "An optional comment associated with the alert's dismissal.",
            "nullable": true,
            "maxLength": 280
        },
        "fixed_at": {
            "$ref": "#/components/schemas/alert-fixed-at"
        },
        "auto_dismissed_at": {
            "$ref": "#/components/schemas/alert-auto-dismissed-at"
        }
    },
    "required": [
        "number",
        "state",
        "dependency",
        "security_advisory",
        "security_vulnerability",
        "url",
        "html_url",
        "created_at",
        "updated_at",
        "dismissed_at",
        "dismissed_by",
        "dismissed_reason",
        "dismissed_comment",
        "fixed_at"
    ],
    "additionalProperties": false
}
```

### `#/components/examples/dependabot-alerts-for-repository`

```json
{
    "value": [
        {
            "number": 2,
            "state": "dismissed",
            "dependency": {
                "package": {
                    "ecosystem": "pip",
                    "name": "django"
                },
                "manifest_path": "path/to/requirements.txt",
                "scope": "runtime"
            },
            "security_advisory": {
                "ghsa_id": "GHSA-rf4j-j272-fj86",
                "cve_id": "CVE-2018-6188",
                "summary": "Django allows remote attackers to obtain potentially sensitive information by leveraging data exposure from the confirm_login_allowed() method, as demonstrated by discovering whether a user account is inactive",
                "description": "django.contrib.auth.forms.AuthenticationForm in Django 2.0 before 2.0.2, and 1.11.8 and 1.11.9, allows remote attackers to obtain potentially sensitive information by leveraging data exposure from the confirm_login_allowed() method, as demonstrated by discovering whether a user account is inactive.",
                "vulnerabilities": [
                    {
                        "package": {
                            "ecosystem": "pip",
                            "name": "django"
                        },
                        "severity": "high",
                        "vulnerable_version_range": ">= 2.0.0, < 2.0.2",
                        "first_patched_version": {
                            "identifier": "2.0.2"
                        }
                    },
                    {
                        "package": {
                            "ecosystem": "pip",
                            "name": "django"
                        },
                        "severity": "high",
                        "vulnerable_version_range": ">= 1.11.8, < 1.11.10",
                        "first_patched_version": {
                            "identifier": "1.11.10"
                        }
                    }
                ],
                "severity": "high",
                "cvss": {
                    "vector_string": "CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:N/A:N",
                    "score": 7.5
                },
                "cwes": [
                    {
                        "cwe_id": "CWE-200",
                        "name": "Exposure of Sensitive Information to an Unauthorized Actor"
                    }
                ],
                "identifiers": [
                    {
                        "type": "GHSA",
                        "value": "GHSA-rf4j-j272-fj86"
                    },
                    {
                        "type": "CVE",
                        "value": "CVE-2018-6188"
                    }
                ],
                "references": [
                    {
                        "url": "https://nvd.nist.gov/vuln/detail/CVE-2018-6188"
                    },
                    {
                        "url": "https://github.com/advisories/GHSA-rf4j-j272-fj86"
                    },
                    {
                        "url": "https://usn.ubuntu.com/3559-1/"
                    },
                    {
                        "url": "https://www.djangoproject.com/weblog/2018/feb/01/security-releases/"
                    },
                    {
                        "url": "http://www.securitytracker.com/id/1040422"
                    }
                ],
                "published_at": "2018-10-03T21:13:54Z",
                "updated_at": "2022-04-26T18:35:37Z",
                "withdrawn_at": null
            },
            "security_vulnerability": {
                "package": {
                    "ecosystem": "pip",
                    "name": "django"
                },
                "severity": "high",
                "vulnerable_version_range": ">= 2.0.0, < 2.0.2",
                "first_patched_version": {
                    "identifier": "2.0.2"
                }
            },
            "url": "https://api.github.com/repos/octocat/hello-world/dependabot/alerts/2",
            "html_url": "https://github.com/octocat/hello-world/security/dependabot/2",
            "created_at": "2022-06-15T07:43:03Z",
            "updated_at": "2022-08-23T14:29:47Z",
            "dismissed_at": "2022-08-23T14:29:47Z",
            "dismissed_by": {
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
            "dismissed_reason": "tolerable_risk",
            "dismissed_comment": "This alert is accurate but we use a sanitizer.",
            "fixed_at": null
        },
        {
            "number": 1,
            "state": "open",
            "dependency": {
                "package": {
                    "ecosystem": "pip",
                    "name": "ansible"
                },
                "manifest_path": "path/to/requirements.txt",
                "scope": "runtime"
            },
            "security_advisory": {
                "ghsa_id": "GHSA-8f4m-hccc-8qph",
                "cve_id": "CVE-2021-20191",
                "summary": "Insertion of Sensitive Information into Log File in ansible",
                "description": "A flaw was found in ansible. Credentials, such as secrets, are being disclosed in console log by default and not protected by no_log feature when using those modules. An attacker can take advantage of this information to steal those credentials. The highest threat from this vulnerability is to data confidentiality.",
                "vulnerabilities": [
                    {
                        "package": {
                            "ecosystem": "pip",
                            "name": "ansible"
                        },
                        "severity": "medium",
                        "vulnerable_version_range": ">= 2.9.0, < 2.9.18",
                        "first_patched_version": {
                            "identifier": "2.9.18"
                        }
                    },
                    {
                        "package": {
                            "ecosystem": "pip",
                            "name": "ansible"
                        },
                        "severity": "medium",
                        "vulnerable_version_range": "< 2.8.19",
                        "first_patched_version": {
                            "identifier": "2.8.19"
                        }
                    },
                    {
                        "package": {
                            "ecosystem": "pip",
                            "name": "ansible"
                        },
                        "severity": "medium",
                        "vulnerable_version_range": ">= 2.10.0, < 2.10.7",
                        "first_patched_version": {
                            "identifier": "2.10.7"
                        }
                    }
                ],
                "severity": "medium",
                "cvss": {
                    "vector_string": "CVSS:3.1/AV:L/AC:L/PR:L/UI:N/S:U/C:H/I:N/A:N",
                    "score": 5.5
                },
                "cwes": [
                    {
                        "cwe_id": "CWE-532",
                        "name": "Insertion of Sensitive Information into Log File"
                    }
                ],
                "identifiers": [
                    {
                        "type": "GHSA",
                        "value": "GHSA-8f4m-hccc-8qph"
                    },
                    {
                        "type": "CVE",
                        "value": "CVE-2021-20191"
                    }
                ],
                "references": [
                    {
                        "url": "https://nvd.nist.gov/vuln/detail/CVE-2021-20191"
                    },
                    {
                        "url": "https://access.redhat.com/security/cve/cve-2021-20191"
                    },
                    {
                        "url": "https://bugzilla.redhat.com/show_bug.cgi?id=1916813"
                    }
                ],
                "published_at": "2021-06-01T17:38:00Z",
                "updated_at": "2021-08-12T23:06:00Z",
                "withdrawn_at": null
            },
            "security_vulnerability": {
                "package": {
                    "ecosystem": "pip",
                    "name": "ansible"
                },
                "severity": "medium",
                "vulnerable_version_range": "< 2.8.19",
                "first_patched_version": {
                    "identifier": "2.8.19"
                }
            },
            "url": "https://api.github.com/repos/octocat/hello-world/dependabot/alerts/1",
            "html_url": "https://github.com/octocat/hello-world/security/dependabot/1",
            "created_at": "2022-06-14T15:21:52Z",
            "updated_at": "2022-06-14T15:21:52Z",
            "dismissed_at": null,
            "dismissed_by": null,
            "dismissed_reason": null,
            "dismissed_comment": null,
            "fixed_at": null
        }
    ]
}
```

### `#/components/responses/not_modified`

```json
{
    "description": "Not modified"
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

### `#/components/responses/validation_failed_simple`

```json
{
    "description": "Validation failed, or the endpoint has been spammed.",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/validation-error-simple"
            }
        }
    }
}
```