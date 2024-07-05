# Get the status of a GitHub Pages deployment

Gets the current status of a GitHub Pages deployment.

The authenticated user must have read permission for the GitHub Pages site.

## Operation Object

```json
{
    "summary": "Get the status of a GitHub Pages deployment",
    "description": "Gets the current status of a GitHub Pages deployment.\n\nThe authenticated user must have read permission for the GitHub Pages site.",
    "tags": [
        "repos"
    ],
    "operationId": "repos/get-pages-deployment",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/pages/pages#get-the-status-of-a-github-pages-deployment"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "$ref": "#/components/parameters/pages-deployment-id"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/pages-deployment-status"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/pages-deployment-status"
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
        "enabledForGitHubApps": true,
        "category": "pages",
        "subcategory": "pages"
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

### `#/components/parameters/pages-deployment-id`

```json
{
    "name": "pages_deployment_id",
    "description": "The ID of the Pages deployment. You can also give the commit SHA of the deployment.",
    "in": "path",
    "required": true,
    "schema": {
        "oneOf": [
            {
                "type": "integer"
            },
            {
                "type": "string"
            }
        ]
    }
}
```

### `#/components/schemas/pages-deployment-status`

```json
{
    "title": "GitHub Pages deployment status",
    "type": "object",
    "properties": {
        "status": {
            "type": "string",
            "description": "The current status of the deployment.",
            "enum": [
                "deployment_in_progress",
                "syncing_files",
                "finished_file_sync",
                "updating_pages",
                "purging_cdn",
                "deployment_cancelled",
                "deployment_failed",
                "deployment_content_failed",
                "deployment_attempt_error",
                "deployment_lost",
                "succeed"
            ]
        }
    }
}
```

### `#/components/examples/pages-deployment-status`

```json
{
    "value": {
        "status": "succeed"
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