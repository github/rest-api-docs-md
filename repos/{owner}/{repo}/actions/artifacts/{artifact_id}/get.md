# Get an artifact

Gets a specific artifact for a workflow run.

Anyone with read access to the repository can use this endpoint.

If the repository is private, OAuth tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "Get an artifact",
    "description": "Gets a specific artifact for a workflow run.\n\nAnyone with read access to the repository can use this endpoint.\n\nIf the repository is private, OAuth tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.",
    "tags": [
        "actions"
    ],
    "operationId": "actions/get-artifact",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/actions/artifacts#get-an-artifact"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "$ref": "#/components/parameters/artifact-id"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/artifact"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/artifact"
                        }
                    }
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

### `#/components/parameters/artifact-id`

```json
{
    "name": "artifact_id",
    "description": "The unique identifier of the artifact.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "integer"
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

### `#/components/examples/artifact`

```json
{
    "value": {
        "id": 11,
        "node_id": "MDg6QXJ0aWZhY3QxMQ==",
        "name": "Rails",
        "size_in_bytes": 556,
        "url": "https://api.github.com/repos/octo-org/octo-docs/actions/artifacts/11",
        "archive_download_url": "https://api.github.com/repos/octo-org/octo-docs/actions/artifacts/11/zip",
        "expired": false,
        "created_at": "2020-01-10T14:59:22Z",
        "expires_at": "2020-01-21T14:59:22Z",
        "updated_at": "2020-01-21T14:59:22Z",
        "workflow_run": {
            "id": 2332938,
            "repository_id": 1296269,
            "head_repository_id": 1296269,
            "head_branch": "main",
            "head_sha": "328faa0536e6fef19753d9d91dc96a9931694ce3"
        }
    }
}
```