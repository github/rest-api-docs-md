# Get a code scanning alert

Gets a single code scanning alert.

OAuth app tokens and personal access tokens (classic) need the `security_events` scope to use this endpoint with private or public repositories, or the `public_repo` scope to use this endpoint with only public repositories.

## Operation Object

```json
{
    "summary": "Get a code scanning alert",
    "description": "Gets a single code scanning alert.\n\nOAuth app tokens and personal access tokens (classic) need the `security_events` scope to use this endpoint with private or public repositories, or the `public_repo` scope to use this endpoint with only public repositories.",
    "tags": [
        "code-scanning"
    ],
    "operationId": "code-scanning/get-alert",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/code-scanning/code-scanning#get-a-code-scanning-alert"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "$ref": "#/components/parameters/alert-number"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/code-scanning-alert"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/code-scanning-alert"
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

### `#/components/parameters/alert-number`

```json
{
    "name": "alert_number",
    "in": "path",
    "description": "The number that identifies an alert. You can find this at the end of the URL for a code scanning alert within GitHub, and in the `number` field in the response from the `GET /repos/{owner}/{repo}/code-scanning/alerts` operation.",
    "required": true,
    "schema": {
        "$ref": "#/components/schemas/alert-number"
    }
}
```

### `#/components/schemas/code-scanning-alert`

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
            "$ref": "#/components/schemas/code-scanning-alert-rule"
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

### `#/components/examples/code-scanning-alert`

```json
{
    "value": {
        "number": 42,
        "created_at": "2020-06-19T11:21:34Z",
        "url": "https://api.github.com/repos/octocat/hello-world/code-scanning/alerts/42",
        "html_url": "https://github.com/octocat/hello-world/code-scanning/42",
        "state": "dismissed",
        "fixed_at": null,
        "dismissed_by": {
            "login": "octocat",
            "id": 54933897,
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
            "security_severity_level": "high",
            "description": "Arbitrary file write during zip extraction (\"Zip Slip\")",
            "name": "js/zipslip",
            "full_description": "Extracting files from a malicious zip archive without validating that the destination file path is within the destination directory can cause files outside the destination directory to be overwritten.",
            "tags": [
                "security",
                "external/cwe/cwe-022"
            ],
            "help": "# Arbitrary file write during zip extraction (\"Zip Slip\")\\nExtracting files from a malicious zip archive without validating that the destination file path is within the destination directory can cause files outside the destination directory to be overwritten ...",
            "help_uri": "https://codeql.github.com/"
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
            "state": "dismissed",
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
        "instances_url": "https://api.github.com/repos/octocat/hello-world/code-scanning/alerts/42/instances"
    }
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