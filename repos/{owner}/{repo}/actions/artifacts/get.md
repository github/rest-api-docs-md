# List artifacts for a repository

Lists all artifacts for a repository.

Anyone with read access to the repository can use this endpoint.

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint with a private repository.

## Operation Object

```json
{
    "summary": "List artifacts for a repository",
    "description": "Lists all artifacts for a repository.\n\nAnyone with read access to the repository can use this endpoint.\n\nOAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint with a private repository.",
    "tags": [
        "actions"
    ],
    "operationId": "actions/list-artifacts-for-repo",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/actions/artifacts#list-artifacts-for-a-repository"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "$ref": "#/components/parameters/per-page"
        },
        {
            "$ref": "#/components/parameters/page"
        },
        {
            "$ref": "#/components/parameters/artifact-name"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "type": "object",
                        "required": [
                            "total_count",
                            "artifacts"
                        ],
                        "properties": {
                            "total_count": {
                                "type": "integer"
                            },
                            "artifacts": {
                                "type": "array",
                                "items": {
                                    "$ref": "#/components/schemas/artifact"
                                }
                            }
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/artifact-paginated"
                        }
                    }
                }
            },
            "headers": {
                "Link": {
                    "$ref": "#/components/headers/link"
                }
            }
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "actions",
        "subcategory": "artifacts"
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

### `#/components/parameters/artifact-name`

```json
{
    "name": "name",
    "description": "The name field of an artifact. When specified, only artifacts with this name will be returned.",
    "in": "query",
    "required": false,
    "schema": {
        "type": "string"
    }
}
```

### `#/components/schemas/artifact`

```json
{
    "title": "Artifact",
    "description": "An artifact",
    "type": "object",
    "properties": {
        "id": {
            "type": "integer",
            "example": 5
        },
        "node_id": {
            "type": "string",
            "example": "MDEwOkNoZWNrU3VpdGU1"
        },
        "name": {
            "description": "The name of the artifact.",
            "type": "string",
            "example": "AdventureWorks.Framework"
        },
        "size_in_bytes": {
            "description": "The size in bytes of the artifact.",
            "type": "integer",
            "example": 12345
        },
        "url": {
            "type": "string",
            "example": "https://api.github.com/repos/github/hello-world/actions/artifacts/5"
        },
        "archive_download_url": {
            "type": "string",
            "example": "https://api.github.com/repos/github/hello-world/actions/artifacts/5/zip"
        },
        "expired": {
            "description": "Whether or not the artifact has expired.",
            "type": "boolean"
        },
        "created_at": {
            "type": "string",
            "format": "date-time",
            "nullable": true
        },
        "expires_at": {
            "type": "string",
            "format": "date-time",
            "nullable": true
        },
        "updated_at": {
            "type": "string",
            "format": "date-time",
            "nullable": true
        },
        "workflow_run": {
            "type": "object",
            "nullable": true,
            "properties": {
                "id": {
                    "example": 10,
                    "type": "integer"
                },
                "repository_id": {
                    "example": 42,
                    "type": "integer"
                },
                "head_repository_id": {
                    "example": 42,
                    "type": "integer"
                },
                "head_branch": {
                    "example": "main",
                    "type": "string"
                },
                "head_sha": {
                    "example": "009b8a3a9ccbb128af87f9b1c0f4c62e8a304f6d",
                    "type": "string"
                }
            }
        }
    },
    "required": [
        "id",
        "node_id",
        "name",
        "size_in_bytes",
        "url",
        "archive_download_url",
        "expired",
        "created_at",
        "expires_at",
        "updated_at"
    ]
}
```

### `#/components/examples/artifact-paginated`

```json
{
    "value": {
        "total_count": 2,
        "artifacts": [
            {
                "id": 11,
                "node_id": "MDg6QXJ0aWZhY3QxMQ==",
                "name": "Rails",
                "size_in_bytes": 556,
                "url": "https://api.github.com/repos/octo-org/octo-docs/actions/artifacts/11",
                "archive_download_url": "https://api.github.com/repos/octo-org/octo-docs/actions/artifacts/11/zip",
                "expired": false,
                "created_at": "2020-01-10T14:59:22Z",
                "expires_at": "2020-03-21T14:59:22Z",
                "updated_at": "2020-02-21T14:59:22Z",
                "workflow_run": {
                    "id": 2332938,
                    "repository_id": 1296269,
                    "head_repository_id": 1296269,
                    "head_branch": "main",
                    "head_sha": "328faa0536e6fef19753d9d91dc96a9931694ce3"
                }
            },
            {
                "id": 13,
                "node_id": "MDg6QXJ0aWZhY3QxMw==",
                "name": "Test output",
                "size_in_bytes": 453,
                "url": "https://api.github.com/repos/octo-org/octo-docs/actions/artifacts/13",
                "archive_download_url": "https://api.github.com/repos/octo-org/octo-docs/actions/artifacts/13/zip",
                "expired": false,
                "created_at": "2020-01-10T14:59:22Z",
                "expires_at": "2020-03-21T14:59:22Z",
                "updated_at": "2020-02-21T14:59:22Z",
                "workflow_run": {
                    "id": 2332942,
                    "repository_id": 1296269,
                    "head_repository_id": 1296269,
                    "head_branch": "main",
                    "head_sha": "178f4f6090b3fccad4a65b3e83d076a622d59652"
                }
            }
        ]
    }
}
```

### `#/components/headers/link`

```json
{
    "example": "<https://api.github.com/resource?page=2>; rel=\"next\", <https://api.github.com/resource?page=5>; rel=\"last\"",
    "schema": {
        "type": "string"
    }
}
```