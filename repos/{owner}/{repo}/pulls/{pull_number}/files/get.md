# List pull requests files

Lists the files in a specified pull request.

**Note:** Responses include a maximum of 3000 files. The paginated response
returns 30 files per page by default.

This endpoint supports the following custom media types. For more information, see "[Media types](https://docs.github.com/rest/using-the-rest-api/getting-started-with-the-rest-api#media-types)."

- **`application/vnd.github.raw+json`**: Returns the raw markdown body. Response will include `body`. This is the default if you do not pass any specific media type.
- **`application/vnd.github.text+json`**: Returns a text only representation of the markdown body. Response will include `body_text`.
- **`application/vnd.github.html+json`**: Returns HTML rendered from the body's markdown. Response will include `body_html`.
- **`application/vnd.github.full+json`**: Returns raw, text, and HTML representations. Response will include `body`, `body_text`, and `body_html`.

## Operation Object

```json
{
    "summary": "List pull requests files",
    "description": "Lists the files in a specified pull request.\n\n**Note:** Responses include a maximum of 3000 files. The paginated response\nreturns 30 files per page by default.\n\nThis endpoint supports the following custom media types. For more information, see \"[Media types](https://docs.github.com/rest/using-the-rest-api/getting-started-with-the-rest-api#media-types).\"\n\n- **`application/vnd.github.raw+json`**: Returns the raw markdown body. Response will include `body`. This is the default if you do not pass any specific media type.\n- **`application/vnd.github.text+json`**: Returns a text only representation of the markdown body. Response will include `body_text`.\n- **`application/vnd.github.html+json`**: Returns HTML rendered from the body's markdown. Response will include `body_html`.\n- **`application/vnd.github.full+json`**: Returns raw, text, and HTML representations. Response will include `body`, `body_text`, and `body_html`.",
    "tags": [
        "pulls"
    ],
    "operationId": "pulls/list-files",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/pulls/pulls#list-pull-requests-files"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "$ref": "#/components/parameters/pull-number"
        },
        {
            "$ref": "#/components/parameters/per-page"
        },
        {
            "$ref": "#/components/parameters/page"
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
                            "$ref": "#/components/schemas/diff-entry"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/diff-entry-items"
                        }
                    }
                }
            },
            "headers": {
                "Link": {
                    "$ref": "#/components/headers/link"
                }
            }
        },
        "422": {
            "$ref": "#/components/responses/validation_failed"
        },
        "500": {
            "$ref": "#/components/responses/internal_error"
        },
        "503": {
            "$ref": "#/components/responses/service_unavailable"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "pulls",
        "subcategory": "pulls"
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

### `#/components/parameters/pull-number`

```json
{
    "name": "pull_number",
    "description": "The number that identifies the pull request.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "integer"
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

### `#/components/schemas/diff-entry`

```json
{
    "title": "Diff Entry",
    "description": "Diff Entry",
    "type": "object",
    "properties": {
        "sha": {
            "type": "string",
            "example": "bbcd538c8e72b8c175046e27cc8f907076331401"
        },
        "filename": {
            "type": "string",
            "example": "file1.txt"
        },
        "status": {
            "type": "string",
            "enum": [
                "added",
                "removed",
                "modified",
                "renamed",
                "copied",
                "changed",
                "unchanged"
            ],
            "example": "added"
        },
        "additions": {
            "type": "integer",
            "example": 103
        },
        "deletions": {
            "type": "integer",
            "example": 21
        },
        "changes": {
            "type": "integer",
            "example": 124
        },
        "blob_url": {
            "type": "string",
            "format": "uri",
            "example": "https://github.com/octocat/Hello-World/blob/6dcb09b5b57875f334f61aebed695e2e4193db5e/file1.txt"
        },
        "raw_url": {
            "type": "string",
            "format": "uri",
            "example": "https://github.com/octocat/Hello-World/raw/6dcb09b5b57875f334f61aebed695e2e4193db5e/file1.txt"
        },
        "contents_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/repos/octocat/Hello-World/contents/file1.txt?ref=6dcb09b5b57875f334f61aebed695e2e4193db5e"
        },
        "patch": {
            "type": "string",
            "example": "@@ -132,7 +132,7 @@ module Test @@ -1000,7 +1000,7 @@ module Test"
        },
        "previous_filename": {
            "type": "string",
            "example": "file.txt"
        }
    },
    "required": [
        "additions",
        "blob_url",
        "changes",
        "contents_url",
        "deletions",
        "filename",
        "raw_url",
        "sha",
        "status"
    ]
}
```

### `#/components/examples/diff-entry-items`

```json
{
    "value": [
        {
            "sha": "bbcd538c8e72b8c175046e27cc8f907076331401",
            "filename": "file1.txt",
            "status": "added",
            "additions": 103,
            "deletions": 21,
            "changes": 124,
            "blob_url": "https://github.com/octocat/Hello-World/blob/6dcb09b5b57875f334f61aebed695e2e4193db5e/file1.txt",
            "raw_url": "https://github.com/octocat/Hello-World/raw/6dcb09b5b57875f334f61aebed695e2e4193db5e/file1.txt",
            "contents_url": "https://api.github.com/repos/octocat/Hello-World/contents/file1.txt?ref=6dcb09b5b57875f334f61aebed695e2e4193db5e",
            "patch": "@@ -132,7 +132,7 @@ module Test @@ -1000,7 +1000,7 @@ module Test"
        }
    ]
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

### `#/components/responses/internal_error`

```json
{
    "description": "Internal Error",
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