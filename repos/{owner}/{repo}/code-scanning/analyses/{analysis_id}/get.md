# Get a code scanning analysis for a repository

Gets a specified code scanning analysis for a repository.

The default JSON response contains fields that describe the analysis.
This includes the Git reference and commit SHA to which the analysis relates,
the datetime of the analysis, the name of the code scanning tool,
and the number of alerts.

The `rules_count` field in the default response give the number of rules
that were run in the analysis.
For very old analyses this data is not available,
and `0` is returned in this field.

This endpoint supports the following custom media types. For more information, see "[Media types](https://docs.github.com/rest/using-the-rest-api/getting-started-with-the-rest-api#media-types)."

- **`application/sarif+json`**: Instead of returning a summary of the analysis, this endpoint returns a subset of the analysis data that was uploaded. The data is formatted as [SARIF version 2.1.0](https://docs.oasis-open.org/sarif/sarif/v2.1.0/cs01/sarif-v2.1.0-cs01.html). It also returns additional data such as the `github/alertNumber` and `github/alertUrl` properties.

OAuth app tokens and personal access tokens (classic) need the `security_events` scope to use this endpoint with private or public repositories, or the `public_repo` scope to use this endpoint with only public repositories.

## Operation Object

```json
{
    "summary": "Get a code scanning analysis for a repository",
    "description": "Gets a specified code scanning analysis for a repository.\n\nThe default JSON response contains fields that describe the analysis.\nThis includes the Git reference and commit SHA to which the analysis relates,\nthe datetime of the analysis, the name of the code scanning tool,\nand the number of alerts.\n\nThe `rules_count` field in the default response give the number of rules\nthat were run in the analysis.\nFor very old analyses this data is not available,\nand `0` is returned in this field.\n\nThis endpoint supports the following custom media types. For more information, see \"[Media types](https://docs.github.com/rest/using-the-rest-api/getting-started-with-the-rest-api#media-types).\"\n\n- **`application/sarif+json`**: Instead of returning a summary of the analysis, this endpoint returns a subset of the analysis data that was uploaded. The data is formatted as [SARIF version 2.1.0](https://docs.oasis-open.org/sarif/sarif/v2.1.0/cs01/sarif-v2.1.0-cs01.html). It also returns additional data such as the `github/alertNumber` and `github/alertUrl` properties.\n\nOAuth app tokens and personal access tokens (classic) need the `security_events` scope to use this endpoint with private or public repositories, or the `public_repo` scope to use this endpoint with only public repositories.",
    "operationId": "code-scanning/get-analysis",
    "tags": [
        "code-scanning"
    ],
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/code-scanning/code-scanning#get-a-code-scanning-analysis-for-a-repository"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "name": "analysis_id",
            "in": "path",
            "description": "The ID of the analysis, as returned from the `GET /repos/{owner}/{repo}/code-scanning/analyses` operation.",
            "required": true,
            "schema": {
                "type": "integer"
            }
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/code-scanning-analysis"
                    },
                    "examples": {
                        "response": {
                            "$ref": "#/components/examples/code-scanning-analysis-default"
                        }
                    }
                },
                "application/json+sarif": {
                    "schema": {
                        "type": "object",
                        "additionalProperties": true
                    },
                    "examples": {
                        "response": {
                            "$ref": "#/components/examples/code-scanning-analysis-sarif"
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

### `#/components/examples/code-scanning-analysis-default`

```json
{
    "summary": "application/json response",
    "value": {
        "ref": "refs/heads/main",
        "commit_sha": "c18c69115654ff0166991962832dc2bd7756e655",
        "analysis_key": ".github/workflows/codeql-analysis.yml:analyze",
        "environment": "{\"language\":\"javascript\"}",
        "error": "",
        "category": ".github/workflows/codeql-analysis.yml:analyze/language:javascript",
        "created_at": "2021-01-13T11:55:49Z",
        "results_count": 3,
        "rules_count": 67,
        "id": 3602840,
        "url": "https://api.github.com/repos/octocat/hello-world/code-scanning/analyses/201",
        "sarif_id": "47177e22-5596-11eb-80a1-c1e54ef945c6",
        "tool": {
            "name": "CodeQL",
            "guid": null,
            "version": "2.4.0"
        },
        "deletable": true,
        "warning": ""
    }
}
```

### `#/components/examples/code-scanning-analysis-sarif`

```json
{
    "summary": "application/json+sarif response",
    "value": {
        "runs": [
            {
                "tool": {
                    "driver": {
                        "name": "CodeQL",
                        "organization": "GitHub",
                        "semanticVersion": "1.0.0",
                        "rules": [
                            {
                                "id": "js/unused-local-variable",
                                "name": "js/unused-local-variable"
                            }
                        ]
                    }
                },
                "results": [
                    {
                        "guid": "326aa09f-9af8-13cf-9851-3d0e5183ec38",
                        "message": {
                            "text": "Unused variable foo."
                        },
                        "locations": [
                            {
                                "physicalLocation": {
                                    "artifactLocation": {
                                        "uri": "file1.js"
                                    },
                                    "region": {
                                        "startLine": 1
                                    }
                                }
                            }
                        ],
                        "ruleId": "js/unused-local-variable",
                        "properties": [
                            {
                                "github/alertNumber": 2
                            },
                            {
                                "github/alertUrl": "https://api.github.com/repos/monalisa/monalisa/code-scanning/alerts/2"
                            }
                        ]
                    }
                ]
            }
        ]
    }
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