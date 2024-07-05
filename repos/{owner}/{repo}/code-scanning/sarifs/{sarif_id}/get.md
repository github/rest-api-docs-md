# Get information about a SARIF upload

`get /repos/{owner}/{repo}/code-scanning/sarifs/{sarif_id}`

Gets information about a SARIF upload, including the status and the URL of the analysis that was uploaded so that you can retrieve details of the analysis. For more information, see "[Get a code scanning analysis for a repository](/rest/code-scanning/code-scanning#get-a-code-scanning-analysis-for-a-repository)."
OAuth app tokens and personal access tokens (classic) need the `security_events` scope to use this endpoint with private or public repositories, or the `public_repo` scope to use this endpoint with only public repositories.

## Operation Object

```json
{
    "summary": "Get information about a SARIF upload",
    "description": "Gets information about a SARIF upload, including the status and the URL of the analysis that was uploaded so that you can retrieve details of the analysis. For more information, see \"[Get a code scanning analysis for a repository](/rest/code-scanning/code-scanning#get-a-code-scanning-analysis-for-a-repository).\"\nOAuth app tokens and personal access tokens (classic) need the `security_events` scope to use this endpoint with private or public repositories, or the `public_repo` scope to use this endpoint with only public repositories.",
    "operationId": "code-scanning/get-sarif",
    "tags": [
        "code-scanning"
    ],
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/code-scanning/code-scanning#get-information-about-a-sarif-upload"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "name": "sarif_id",
            "description": "The SARIF ID obtained after uploading.",
            "in": "path",
            "schema": {
                "type": "string"
            },
            "required": true
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/code-scanning-sarifs-status"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/code-scanning-sarif-upload-status"
                        }
                    }
                }
            }
        },
        "403": {
            "$ref": "#/components/responses/code_scanning_forbidden_read"
        },
        "404": {
            "description": "Not Found if the sarif id does not match any upload"
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

### `#/components/schemas/code-scanning-sarifs-status`

```json
{
    "type": "object",
    "properties": {
        "processing_status": {
            "type": "string",
            "enum": [
                "pending",
                "complete",
                "failed"
            ],
            "description": "`pending` files have not yet been processed, while `complete` means results from the SARIF have been stored. `failed` files have either not been processed at all, or could only be partially processed."
        },
        "analyses_url": {
            "type": "string",
            "description": "The REST API URL for getting the analyses associated with the upload.",
            "format": "uri",
            "readOnly": true,
            "nullable": true
        },
        "errors": {
            "type": "array",
            "items": {
                "type": "string"
            },
            "description": "Any errors that ocurred during processing of the delivery.",
            "readOnly": true,
            "nullable": true
        }
    }
}
```

### `#/components/examples/code-scanning-sarif-upload-status`

```json
{
    "summary": "Default response",
    "value": {
        "processing_status": "complete",
        "analyses_url": "https://api.github.com/repos/octocat/hello-world/code-scanning/analyses?sarif_id=47177e22-5596-11eb-80a1-c1e54ef945c6"
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