# Get details about a codespace export

`get /user/codespaces/{codespace_name}/exports/{export_id}`

Gets information about an export of a codespace.

OAuth app tokens and personal access tokens (classic) need the `codespace` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "Get details about a codespace export",
    "description": "Gets information about an export of a codespace.\n\nOAuth app tokens and personal access tokens (classic) need the `codespace` scope to use this endpoint.",
    "tags": [
        "codespaces"
    ],
    "operationId": "codespaces/get-export-details-for-authenticated-user",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/codespaces/codespaces#get-details-about-a-codespace-export"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/codespace-name"
        },
        {
            "$ref": "#/components/parameters/export-id"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/codespace-export-details"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/user-export-details"
                        }
                    }
                }
            }
        },
        "404": {
            "$ref": "#/components/responses/not_found"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": false,
        "category": "codespaces",
        "subcategory": "codespaces"
    }
}
```

## References

### `#/components/parameters/codespace-name`

```json
{
    "name": "codespace_name",
    "in": "path",
    "required": true,
    "description": "The name of the codespace.",
    "schema": {
        "type": "string"
    }
}
```

### `#/components/parameters/export-id`

```json
{
    "name": "export_id",
    "in": "path",
    "required": true,
    "description": "The ID of the export operation, or `latest`. Currently only `latest` is currently supported.",
    "schema": {
        "type": "string"
    }
}
```

### `#/components/schemas/codespace-export-details`

```json
{
    "type": "object",
    "title": "Fetches information about an export of a codespace.",
    "description": "An export of a codespace. Also, latest export details for a codespace can be fetched with id = latest",
    "properties": {
        "state": {
            "type": "string",
            "description": "State of the latest export",
            "nullable": true,
            "example": "succeeded | failed | in_progress"
        },
        "completed_at": {
            "description": "Completion time of the last export operation",
            "type": "string",
            "format": "date-time",
            "nullable": true,
            "example": "2021-01-01T19:01:12Z"
        },
        "branch": {
            "type": "string",
            "description": "Name of the exported branch",
            "nullable": true,
            "example": "codespace-monalisa-octocat-hello-world-g4wpq6h95q"
        },
        "sha": {
            "type": "string",
            "description": "Git commit SHA of the exported branch",
            "nullable": true,
            "example": "fd95a81ca01e48ede9f39c799ecbcef817b8a3b2"
        },
        "id": {
            "type": "string",
            "description": "Id for the export details",
            "example": "latest"
        },
        "export_url": {
            "type": "string",
            "description": "Url for fetching export details",
            "example": "https://api.github.com/user/codespaces/:name/exports/latest"
        },
        "html_url": {
            "type": "string",
            "nullable": true,
            "description": "Web url for the exported branch",
            "example": "https://github.com/octocat/hello-world/tree/:branch"
        }
    }
}
```

### `#/components/examples/user-export-details`

```json
{
    "value": {
        "state": "succeeded",
        "completed_at": "2022-01-01T14:59:22Z",
        "branch": "codespace-monalisa-octocat-hello-world-g4wpq6h95q",
        "sha": "fd95a81ca01e48ede9f39c799ecbcef817b8a3b2",
        "id": "latest",
        "export_url": "https://api.github.com/user/codespaces/:name/exports/latest"
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