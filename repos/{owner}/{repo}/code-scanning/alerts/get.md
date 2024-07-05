# List code scanning alerts for a repository

`get /repos/{owner}/{repo}/code-scanning/alerts`

Lists code scanning alerts.

The response includes a `most_recent_instance` object.
This provides details of the most recent instance of this alert
for the default branch (or for the specified Git reference if you used `ref` in the request).

OAuth app tokens and personal access tokens (classic) need the `security_events` scope to use this endpoint with private or public repositories, or the `public_repo` scope to use this endpoint with only public repositories.

## Operation Object

```json
{
    "summary": "List code scanning alerts for a repository",
    "description": "Lists code scanning alerts.\n\nThe response includes a `most_recent_instance` object.\nThis provides details of the most recent instance of this alert\nfor the default branch (or for the specified Git reference if you used `ref` in the request).\n\nOAuth app tokens and personal access tokens (classic) need the `security_events` scope to use this endpoint with private or public repositories, or the `public_repo` scope to use this endpoint with only public repositories.",
    "tags": [
        "code-scanning"
    ],
    "operationId": "code-scanning/list-alerts-for-repo",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/code-scanning/code-scanning#list-code-scanning-alerts-for-a-repository"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "$ref": "#/components/parameters/tool-name"
        },
        {
            "$ref": "#/components/parameters/tool-guid"
        },
        {
            "$ref": "#/components/parameters/page"
        },
        {
            "$ref": "#/components/parameters/per-page"
        },
        {
            "$ref": "#/components/parameters/git-ref"
        },
        {
            "$ref": "#/components/parameters/direction"
        },
        {
            "name": "sort",
            "description": "The property by which to sort the results.",
            "in": "query",
            "required": false,
            "schema": {
                "type": "string",
                "enum": [
                    "created",
                    "updated"
                ],
                "default": "created"
            }
        },
        {
            "name": "state",
            "description": "If specified, only code scanning alerts with this state will be returned.",
            "in": "query",
            "required": false,
            "schema": {
                "$ref": "#/components/schemas/code-scanning-alert-state-query"
            }
        },
        {
            "name": "severity",
            "description": "If specified, only code scanning alerts with this severity will be returned.",
            "in": "query",
            "required": false,
            "schema": {
                "$ref": "#/components/schemas/code-scanning-alert-severity"
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
                            "$ref": "#/components/schemas/code-scanning-alert-items"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/code-scanning-alert-items"
                        }
                    }
                }
            }
        },
        "304": {
            "$ref": "#/components/responses/not_modified"
        },
        "403": {
            "$ref": "#/components/responses/code_scanning_forbidden_read"
        },
        "404": {
            "$ref": "#/components/responses/not_found"
        },
        "503": {
            "$ref": "#/components/responses/service_unavailable"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "code-scanning",
        "subcategory": "code-scanning"
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

### `#/components/parameters/tool-name`

```json
{
    "name": "tool_name",
    "description": "The name of a code scanning tool. Only results by this tool will be listed. You can specify the tool by using either `tool_name` or `tool_guid`, but not both.",
    "in": "query",
    "required": false,
    "schema": {
        "$ref": "#/components/schemas/code-scanning-analysis-tool-name"
    }
}
```

### `#/components/parameters/tool-guid`

```json
{
    "name": "tool_guid",
    "description": "The GUID of a code scanning tool. Only results by this tool will be listed. Note that some code scanning tools may not include a GUID in their analysis data. You can specify the tool by using either `tool_guid` or `tool_name`, but not both.",
    "in": "query",
    "required": false,
    "schema": {
        "$ref": "#/components/schemas/code-scanning-analysis-tool-guid"
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

### `#/components/parameters/git-ref`

```json
{
    "name": "ref",
    "description": "The Git reference for the results you want to list. The `ref` for a branch can be formatted either as `refs/heads/<branch name>` or simply `<branch name>`. To reference a pull request use `refs/pull/<number>/merge`.",
    "in": "query",
    "required": false,
    "schema": {
        "$ref": "#/components/schemas/code-scanning-ref"
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

### `#/components/schemas/code-scanning-alert-state-query`

```json
{
    "type": "string",
    "description": "State of a code scanning alert.",
    "enum": [
        "open",
        "closed",
        "dismissed",
        "fixed"
    ]
}
```

### `#/components/schemas/code-scanning-alert-severity`

```json
{
    "type": "string",
    "description": "Severity of a code scanning alert.",
    "enum": [
        "critical",
        "high",
        "medium",
        "low",
        "warning",
        "note",
        "error"
    ]
}
```

### `#/components/schemas/code-scanning-alert-items`

```json
{
    "type": "object",
    "properties": {
        "number": {
            "$ref": "#/components/schemas/alert-number"
        },
        "created_at": {
            "$ref": "#/components/schemas/alert-created-at"
        },
        "updated_at": {
            "$ref": "#/components/schemas/alert-updated-at"
        },
        "url": {
            "$ref": "#/components/schemas/alert-url"
        },
        "html_url": {
            "$ref": "#/components/schemas/alert-html-url"
        },
        "instances_url": {
            "$ref": "#/components/schemas/alert-instances-url"
        },
        "state": {
            "$ref": "#/components/schemas/code-scanning-alert-state"
        },
        "fixed_at": {
            "$ref": "#/components/schemas/alert-fixed-at"
        },
        "dismissed_by": {
            "$ref": "#/components/schemas/nullable-simple-user"
        },
        "dismissed_at": {
            "$ref": "#/components/schemas/alert-dismissed-at"
        },
        "dismissed_reason": {
            "$ref": "#/components/schemas/code-scanning-alert-dismissed-reason"
        },
        "dismissed_comment": {
            "$ref": "#/components/schemas/code-scanning-alert-dismissed-comment"
        },
        "rule": {
            "$ref": "#/components/schemas/code-scanning-alert-rule-summary"
        },
        "tool": {
            "$ref": "#/components/schemas/code-scanning-analysis-tool"
        },
        "most_recent_instance": {
            "$ref": "#/components/schemas/code-scanning-alert-instance"
        }
    },
    "required": [
        "number",
        "created_at",
        "url",
        "html_url",
        "instances_url",
        "state",
        "dismissed_by",
        "dismissed_at",
        "dismissed_reason",
        "rule",
        "tool",
        "most_recent_instance"
    ]
}
```

### `#/components/examples/code-scanning-alert-items`

```json
{
    "value": [
        {
            "number": 4,
            "created_at": "2020-02-13T12:29:18Z",
            "url": "https://api.github.com/repos/octocat/hello-world/code-scanning/alerts/4",
            "html_url": "https://github.com/octocat/hello-world/code-scanning/4",
            "state": "open",
            "fixed_at": null,
            "dismissed_by": null,
            "dismissed_at": null,
            "dismissed_reason": null,
            "dismissed_comment": null,
            "rule": {
                "id": "js/zipslip",
                "severity": "error",
                "tags": [
                    "security",
                    "external/cwe/cwe-022"
                ],
                "description": "Arbitrary file write during zip extraction",
                "name": "js/zipslip"
            },
            "tool": {
                "name": "CodeQL",
                "guid": null,
                "version": "2.4.0"
            },
            "most_recent_instance": {
                "ref": "refs/heads/main",
                "analysis_key": ".github/workflows/codeql-analysis.yml:CodeQL-Build",
                "category": ".github/workflows/codeql-analysis.yml:CodeQL-Build",
                "environment": "{}",
                "state": "open",
                "commit_sha": "39406e42cb832f683daa691dd652a8dc36ee8930",
                "message": {
                    "text": "This path depends on a user-provided value."
                },
                "location": {
                    "path": "spec-main/api-session-spec.ts",
                    "start_line": 917,
                    "end_line": 917,
                    "start_column": 7,
                    "end_column": 18
                },
                "classifications": [
                    "test"
                ]
            },
            "instances_url": "https://api.github.com/repos/octocat/hello-world/code-scanning/alerts/4/instances"
        },
        {
            "number": 3,
            "created_at": "2020-02-13T12:29:18Z",
            "url": "https://api.github.com/repos/octocat/hello-world/code-scanning/alerts/3",
            "html_url": "https://github.com/octocat/hello-world/code-scanning/3",
            "state": "dismissed",
            "fixed_at": null,
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
            "dismissed_at": "2020-02-14T12:29:18Z",
            "dismissed_reason": "false positive",
            "dismissed_comment": "This alert is not actually correct, because there's a sanitizer included in the library.",
            "rule": {
                "id": "js/zipslip",
                "severity": "error",
                "tags": [
                    "security",
                    "external/cwe/cwe-022"
                ],
                "description": "Arbitrary file write during zip extraction",
                "name": "js/zipslip"
            },
            "tool": {
                "name": "CodeQL",
                "guid": null,
                "version": "2.4.0"
            },
            "most_recent_instance": {
                "ref": "refs/heads/main",
                "analysis_key": ".github/workflows/codeql-analysis.yml:CodeQL-Build",
                "category": ".github/workflows/codeql-analysis.yml:CodeQL-Build",
                "environment": "{}",
                "state": "open",
                "commit_sha": "39406e42cb832f683daa691dd652a8dc36ee8930",
                "message": {
                    "text": "This path depends on a user-provided value."
                },
                "location": {
                    "path": "lib/ab12-gen.js",
                    "start_line": 917,
                    "end_line": 917,
                    "start_column": 7,
                    "end_column": 18
                },
                "classifications": []
            },
            "instances_url": "https://api.github.com/repos/octocat/hello-world/code-scanning/alerts/3/instances"
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

### `#/components/responses/code_scanning_forbidden_read`

```json
{
    "description": "Response if GitHub Advanced Security is not enabled for this repository",
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

### `#/components/responses/service_unavailable`

```json
{
    "description": "Service unavailable",
    "content": {
        "application/json": {
            "schema": {
                "type": "object",
                "properties": {
                    "code": {
                        "type": "string"
                    },
                    "message": {
                        "type": "string"
                    },
                    "documentation_url": {
                        "type": "string"
                    }
                }
            }
        }
    }
}
```