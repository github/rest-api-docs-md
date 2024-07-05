# Get all API versions

Get all supported GitHub API versions.

## Operation Object

```json
{
    "summary": "Get all API versions",
    "description": "Get all supported GitHub API versions.",
    "tags": [
        "meta"
    ],
    "operationId": "meta/get-all-versions",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/meta/meta#get-all-api-versions"
    },
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "type": "array",
                        "items": {
                            "type": "string",
                            "format": "date",
                            "example": "2021-01-01"
                        }
                    },
                    "examples": {
                        "default": {
                            "value": [
                                "2021-01-01",
                                "2021-06-01",
                                "2022-01-01"
                            ]
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
        "category": "meta",
        "subcategory": "meta"
    }
}
```

## References

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