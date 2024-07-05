# List code scanning analyses for a repository

Lists the details of all code scanning analyses for a repository,
starting with the most recent.
The response is paginated and you can use the `page` and `per_page` parameters
to list the analyses you're interested in.
By default 30 analyses are listed per page.

The `rules_count` field in the response give the number of rules
that were run in the analysis.
For very old analyses this data is not available,
and `0` is returned in this field.

**Deprecation notice**:
The `tool_name` field is deprecated and will, in future, not be included in the response for this endpoint. The example response reflects this change. The tool name can now be found inside the `tool` field.

OAuth app tokens and personal access tokens (classic) need the `security_events` scope to use this endpoint with private or public repositories, or the `public_repo` scope to use this endpoint with only public repositories.

## Operation Object

```json
{
    "summary": "List code scanning analyses for a repository",
    "description": "Lists the details of all code scanning analyses for a repository,\nstarting with the most recent.\nThe response is paginated and you can use the `page` and `per_page` parameters\nto list the analyses you're interested in.\nBy default 30 analyses are listed per page.\n\nThe `rules_count` field in the response give the number of rules\nthat were run in the analysis.\nFor very old analyses this data is not available,\nand `0` is returned in this field.\n\n**Deprecation notice**:\nThe `tool_name` field is deprecated and will, in future, not be included in the response for this endpoint. The example response reflects this change. The tool name can now be found inside the `tool` field.\n\nOAuth app tokens and personal access tokens (classic) need the `security_events` scope to use this endpoint with private or public repositories, or the `public_repo` scope to use this endpoint with only public repositories.",
    "operationId": "code-scanning/list-recent-analyses",
    "tags": [
        "code-scanning"
    ],
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/code-scanning/code-scanning#list-code-scanning-analyses-for-a-repository"
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
            "name": "ref",
            "in": "query",
            "description": "The Git reference for the analyses you want to list. The `ref` for a branch can be formatted either as `refs/heads/<branch name>` or simply `<branch name>`. To reference a pull request use `refs/pull/<number>/merge`.",
            "required": false,
            "schema": {
                "$ref": "#/components/schemas/code-scanning-ref"
            }
        },
        {
            "name": "sarif_id",
            "in": "query",
            "description": "Filter analyses belonging to the same SARIF upload.",
            "required": false,
            "schema": {
                "$ref": "#/components/schemas/code-scanning-analysis-sarif-id"
            }
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
                    "created"
                ],
                "default": "created"
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
                            "$ref": "#/components/schemas/code-scanning-analysis"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/code-scanning-analysis-items"
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
        "enabledForGitHubApps": true,
        "githubCloudOnly": false,
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

### `#/components/schemas/code-scanning-ref`

```json
{
    "type": "string",
    "description": "The Git reference, formatted as `refs/pull/<number>/merge`, `refs/pull/<number>/head`,\n`refs/heads/<branch name>` or simply `<branch name>`."
}
```

### `#/components/schemas/code-scanning-analysis-sarif-id`

```json
{
    "type": "string",
    "description": "An identifier for the upload.",
    "example": "6c81cd8e-b078-4ac3-a3be-1dad7dbd0b53"
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

### `#/components/schemas/code-scanning-analysis`

```json
{
    "type": "object",
    "properties": {
        "ref": {
            "$ref": "#/components/schemas/code-scanning-ref"
        },
        "commit_sha": {
            "$ref": "#/components/schemas/code-scanning-analysis-commit-sha"
        },
        "analysis_key": {
            "$ref": "#/components/schemas/code-scanning-analysis-analysis-key"
        },
        "environment": {
            "$ref": "#/components/schemas/code-scanning-analysis-environment"
        },
        "category": {
            "$ref": "#/components/schemas/code-scanning-analysis-category"
        },
        "error": {
            "type": "string",
            "example": "error reading field xyz"
        },
        "created_at": {
            "$ref": "#/components/schemas/code-scanning-analysis-created-at"
        },
        "results_count": {
            "type": "integer",
            "description": "The total number of results in the analysis."
        },
        "rules_count": {
            "type": "integer",
            "description": "The total number of rules used in the analysis."
        },
        "id": {
            "type": "integer",
            "description": "Unique identifier for this analysis."
        },
        "url": {
            "$ref": "#/components/schemas/code-scanning-analysis-url"
        },
        "sarif_id": {
            "$ref": "#/components/schemas/code-scanning-analysis-sarif-id"
        },
        "tool": {
            "$ref": "#/components/schemas/code-scanning-analysis-tool"
        },
        "deletable": {
            "type": "boolean"
        },
        "warning": {
            "type": "string",
            "description": "Warning generated when processing the analysis",
            "example": "123 results were ignored"
        }
    },
    "required": [
        "ref",
        "commit_sha",
        "analysis_key",
        "environment",
        "error",
        "created_at",
        "results_count",
        "rules_count",
        "id",
        "url",
        "sarif_id",
        "tool",
        "deletable",
        "warning"
    ]
}
```

### `#/components/examples/code-scanning-analysis-items`

```json
{
    "value": [
        {
            "ref": "refs/heads/main",
            "commit_sha": "d99612c3e1f2970085cfbaeadf8f010ef69bad83",
            "analysis_key": ".github/workflows/codeql-analysis.yml:analyze",
            "environment": "{\"language\":\"python\"}",
            "error": "",
            "category": ".github/workflows/codeql-analysis.yml:analyze/language:python",
            "created_at": "2020-08-27T15:05:21Z",
            "results_count": 17,
            "rules_count": 49,
            "id": 201,
            "url": "https://api.github.com/repos/octocat/hello-world/code-scanning/analyses/201",
            "sarif_id": "6c81cd8e-b078-4ac3-a3be-1dad7dbd0b53",
            "tool": {
                "name": "CodeQL",
                "guid": null,
                "version": "2.4.0"
            },
            "deletable": true,
            "warning": ""
        },
        {
            "ref": "refs/heads/my-branch",
            "commit_sha": "c8cff6510d4d084fb1b4aa13b64b97ca12b07321",
            "analysis_key": ".github/workflows/shiftleft.yml:build",
            "environment": "{}",
            "error": "",
            "category": ".github/workflows/shiftleft.yml:build/",
            "created_at": "2020-08-31T22:46:44Z",
            "results_count": 17,
            "rules_count": 32,
            "id": 200,
            "url": "https://api.github.com/repos/octocat/hello-world/code-scanning/analyses/200",
            "sarif_id": "8981cd8e-b078-4ac3-a3be-1dad7dbd0b582",
            "tool": {
                "name": "Python Security Analysis",
                "guid": null,
                "version": "1.2.0"
            },
            "deletable": true,
            "warning": ""
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