# List instances of a code scanning alert

Lists all instances of the specified code scanning alert.

OAuth app tokens and personal access tokens (classic) need the `security_events` scope to use this endpoint with private or public repositories, or the `public_repo` scope to use this endpoint with only public repositories.

## Operation Object

```json
{
    "summary": "List instances of a code scanning alert",
    "description": "Lists all instances of the specified code scanning alert.\n\nOAuth app tokens and personal access tokens (classic) need the `security_events` scope to use this endpoint with private or public repositories, or the `public_repo` scope to use this endpoint with only public repositories.",
    "tags": [
        "code-scanning"
    ],
    "operationId": "code-scanning/list-alert-instances",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/code-scanning/code-scanning#list-instances-of-a-code-scanning-alert"
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
        },
        {
            "$ref": "#/components/parameters/page"
        },
        {
            "$ref": "#/components/parameters/per-page"
        },
        {
            "$ref": "#/components/parameters/git-ref"
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
                            "$ref": "#/components/schemas/code-scanning-alert-instance"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/code-scanning-alert-instances"
                        }
                    }
                }
            }
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

### `#/components/schemas/code-scanning-alert-instance`

```json
{
    "type": "object",
    "properties": {
        "ref": {
            "$ref": "#/components/schemas/code-scanning-ref"
        },
        "analysis_key": {
            "$ref": "#/components/schemas/code-scanning-analysis-analysis-key"
        },
        "environment": {
            "$ref": "#/components/schemas/code-scanning-alert-environment"
        },
        "category": {
            "$ref": "#/components/schemas/code-scanning-analysis-category"
        },
        "state": {
            "$ref": "#/components/schemas/code-scanning-alert-state"
        },
        "commit_sha": {
            "type": "string"
        },
        "message": {
            "type": "object",
            "properties": {
                "text": {
                    "type": "string"
                }
            }
        },
        "location": {
            "$ref": "#/components/schemas/code-scanning-alert-location"
        },
        "html_url": {
            "type": "string"
        },
        "classifications": {
            "type": "array",
            "description": "Classifications that have been applied to the file that triggered the alert.\nFor example identifying it as documentation, or a generated file.",
            "items": {
                "$ref": "#/components/schemas/code-scanning-alert-classification"
            }
        }
    }
}
```

### `#/components/examples/code-scanning-alert-instances`

```json
{
    "value": [
        {
            "ref": "refs/heads/main",
            "analysis_key": ".github/workflows/codeql-analysis.yml:CodeQL-Build",
            "environment": "",
            "category": ".github/workflows/codeql-analysis.yml:CodeQL-Build",
            "state": "open",
            "fixed_at": null,
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
            "classifications": [
                "library"
            ]
        },
        {
            "ref": "refs/pull/3740/merge",
            "analysis_key": ".github/workflows/codeql-analysis.yml:CodeQL-Build",
            "environment": "",
            "category": ".github/workflows/codeql-analysis.yml:CodeQL-Build",
            "state": "fixed",
            "fixed_at": "2020-02-14T12:29:18Z",
            "commit_sha": "b09da05606e27f463a2b49287684b4ae777092f2",
            "message": {
                "text": "This suffix check is missing a length comparison to correctly handle lastIndexOf returning -1."
            },
            "location": {
                "path": "app/script.js",
                "start_line": 2,
                "end_line": 2,
                "start_column": 10,
                "end_column": 50
            },
            "classifications": [
                "source"
            ]
        }
    ]
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