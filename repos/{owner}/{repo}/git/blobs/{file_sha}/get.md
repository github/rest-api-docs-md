# Get a blob

`get /repos/{owner}/{repo}/git/blobs/{file_sha}`

The `content` in the response will always be Base64 encoded.

This endpoint supports the following custom media types. For more information, see "[Media types](https://docs.github.com/rest/using-the-rest-api/getting-started-with-the-rest-api#media-types)."

- **`application/vnd.github.raw+json`**: Returns the raw blob data.
- **`application/vnd.github+json`**: Returns a JSON representation of the blob with `content` as a base64 encoded string. This is the default if no media type is specified.

**Note** This endpoint supports blobs up to 100 megabytes in size.

## Operation Object

```json
{
    "summary": "Get a blob",
    "description": "The `content` in the response will always be Base64 encoded.\n\nThis endpoint supports the following custom media types. For more information, see \"[Media types](https://docs.github.com/rest/using-the-rest-api/getting-started-with-the-rest-api#media-types).\"\n\n- **`application/vnd.github.raw+json`**: Returns the raw blob data.\n- **`application/vnd.github+json`**: Returns a JSON representation of the blob with `content` as a base64 encoded string. This is the default if no media type is specified.\n\n**Note** This endpoint supports blobs up to 100 megabytes in size.",
    "tags": [
        "git"
    ],
    "operationId": "git/get-blob",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/git/blobs#get-a-blob"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "name": "file_sha",
            "in": "path",
            "required": true,
            "schema": {
                "type": "string"
            }
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/blob"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/blob"
                        }
                    }
                }
            }
        },
        "404": {
            "$ref": "#/components/responses/not_found"
        },
        "422": {
            "$ref": "#/components/responses/validation_failed"
        },
        "403": {
            "$ref": "#/components/responses/forbidden"
        },
        "409": {
            "$ref": "#/components/responses/conflict"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "git",
        "subcategory": "blobs"
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

### `#/components/schemas/blob`

```json
{
    "title": "Blob",
    "description": "Blob",
    "type": "object",
    "properties": {
        "content": {
            "type": "string"
        },
        "encoding": {
            "type": "string"
        },
        "url": {
            "type": "string",
            "format": "uri"
        },
        "sha": {
            "type": "string"
        },
        "size": {
            "type": "integer",
            "nullable": true
        },
        "node_id": {
            "type": "string"
        },
        "highlighted_content": {
            "type": "string"
        }
    },
    "required": [
        "sha",
        "url",
        "node_id",
        "size",
        "content",
        "encoding"
    ]
}
```

### `#/components/examples/blob`

```json
{
    "value": {
        "content": "Q29udGVudCBvZiB0aGUgYmxvYg==",
        "encoding": "base64",
        "url": "https://api.github.com/repos/octocat/example/git/blobs/3a0f86fb8db8eea7ccbb9a95f325ddbedfb25e15",
        "sha": "3a0f86fb8db8eea7ccbb9a95f325ddbedfb25e15",
        "size": 19,
        "node_id": "Q29udGVudCBvZiB0aGUgYmxvYg=="
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

### `#/components/responses/validation_failed`

```json
{
    "description": "Validation failed, or the endpoint has been spammed.",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/validation-error"
            }
        }
    }
}
```

### `#/components/responses/forbidden`

```json
{
    "description": "Forbidden",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/basic-error"
            }
        }
    }
}
```

### `#/components/responses/conflict`

```json
{
    "description": "Conflict",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/basic-error"
            }
        }
    }
}
```