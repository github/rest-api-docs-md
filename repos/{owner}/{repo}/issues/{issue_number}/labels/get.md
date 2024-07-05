# List labels for an issue

Lists all labels for an issue.

## Operation Object

```json
{
    "summary": "List labels for an issue",
    "description": "Lists all labels for an issue.",
    "tags": [
        "issues"
    ],
    "operationId": "issues/list-labels-on-issue",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/issues/labels#list-labels-for-an-issue"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "$ref": "#/components/parameters/issue-number"
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
                            "$ref": "#/components/schemas/label"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/label-items"
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
        "301": {
            "$ref": "#/components/responses/moved_permanently"
        },
        "404": {
            "$ref": "#/components/responses/not_found"
        },
        "410": {
            "$ref": "#/components/responses/gone"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "issues",
        "subcategory": "labels"
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

### `#/components/parameters/issue-number`

```json
{
    "name": "issue_number",
    "description": "The number that identifies the issue.",
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

### `#/components/schemas/label`

```json
{
    "title": "Label",
    "description": "Color-coded labels help you categorize and filter your issues (just like labels in Gmail).",
    "type": "object",
    "properties": {
        "id": {
            "type": "integer",
            "format": "int64",
            "example": 208045946
        },
        "node_id": {
            "type": "string",
            "example": "MDU6TGFiZWwyMDgwNDU5NDY="
        },
        "url": {
            "description": "URL for the label",
            "example": "https://api.github.com/repositories/42/labels/bug",
            "type": "string",
            "format": "uri"
        },
        "name": {
            "description": "The name of the label.",
            "example": "bug",
            "type": "string"
        },
        "description": {
            "type": "string",
            "example": "Something isn't working",
            "nullable": true
        },
        "color": {
            "description": "6-character hex code, without the leading #, identifying the color",
            "example": "FFFFFF",
            "type": "string"
        },
        "default": {
            "type": "boolean",
            "example": true
        }
    },
    "required": [
        "id",
        "node_id",
        "url",
        "name",
        "description",
        "color",
        "default"
    ]
}
```

### `#/components/examples/label-items`

```json
{
    "value": [
        {
            "id": 208045946,
            "node_id": "MDU6TGFiZWwyMDgwNDU5NDY=",
            "url": "https://api.github.com/repos/octocat/Hello-World/labels/bug",
            "name": "bug",
            "description": "Something isn't working",
            "color": "f29513",
            "default": true
        },
        {
            "id": 208045947,
            "node_id": "MDU6TGFiZWwyMDgwNDU5NDc=",
            "url": "https://api.github.com/repos/octocat/Hello-World/labels/enhancement",
            "name": "enhancement",
            "description": "New feature or request",
            "color": "a2eeef",
            "default": false
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

### `#/components/responses/moved_permanently`

```json
{
    "description": "Moved permanently",
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

### `#/components/responses/gone`

```json
{
    "description": "Gone",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/basic-error"
            }
        }
    }
}
```