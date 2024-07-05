# Get a code scanning default setup configuration

`get /repos/{owner}/{repo}/code-scanning/default-setup`

Gets a code scanning default setup configuration.

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint with private or public repositories, or the `public_repo` scope to use this endpoint with only public repositories.

## Operation Object

```json
{
    "summary": "Get a code scanning default setup configuration",
    "description": "Gets a code scanning default setup configuration.\n\nOAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint with private or public repositories, or the `public_repo` scope to use this endpoint with only public repositories.",
    "tags": [
        "code-scanning"
    ],
    "operationId": "code-scanning/get-default-setup",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/code-scanning/code-scanning#get-a-code-scanning-default-setup-configuration"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/code-scanning-default-setup"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/code-scanning-default-setup"
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

### `#/components/schemas/code-scanning-default-setup`

```json
{
    "description": "Configuration for code scanning default setup.",
    "type": "object",
    "properties": {
        "state": {
            "description": "Code scanning default setup has been configured or not.",
            "type": "string",
            "enum": [
                "configured",
                "not-configured"
            ]
        },
        "languages": {
            "description": "Languages to be analyzed.",
            "type": "array",
            "items": {
                "type": "string",
                "enum": [
                    "c-cpp",
                    "csharp",
                    "go",
                    "java-kotlin",
                    "javascript-typescript",
                    "javascript",
                    "python",
                    "ruby",
                    "typescript",
                    "swift"
                ]
            }
        },
        "query_suite": {
            "description": "CodeQL query suite to be used.",
            "type": "string",
            "enum": [
                "default",
                "extended"
            ]
        },
        "updated_at": {
            "description": "Timestamp of latest configuration update.",
            "nullable": true,
            "type": "string",
            "format": "date-time",
            "example": "2023-12-06T14:20:20.000Z"
        },
        "schedule": {
            "description": "The frequency of the periodic analysis.",
            "nullable": true,
            "type": "string",
            "enum": [
                "weekly"
            ]
        }
    }
}
```

### `#/components/examples/code-scanning-default-setup`

```json
{
    "value": {
        "state": "configured",
        "languages": [
            "ruby",
            "python"
        ],
        "query_suite": "default",
        "updated_at": "2023-01-19T11:21:34Z",
        "schedule": "weekly"
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