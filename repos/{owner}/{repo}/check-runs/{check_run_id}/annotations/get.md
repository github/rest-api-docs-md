# List check run annotations

Lists annotations for a check run using the annotation `id`.

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint on a private repository.

## Operation Object

```json
{
    "summary": "List check run annotations",
    "description": "Lists annotations for a check run using the annotation `id`.\n\nOAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint on a private repository.",
    "tags": [
        "checks"
    ],
    "operationId": "checks/list-annotations",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/checks/runs#list-check-run-annotations"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "$ref": "#/components/parameters/check-run-id"
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
                            "$ref": "#/components/schemas/check-annotation"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/check-annotation-items"
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
        "category": "checks",
        "subcategory": "runs"
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

### `#/components/parameters/check-run-id`

```json
{
    "name": "check_run_id",
    "description": "The unique identifier of the check run.",
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

### `#/components/schemas/check-annotation`

```json
{
    "title": "Check Annotation",
    "description": "Check Annotation",
    "type": "object",
    "properties": {
        "path": {
            "type": "string",
            "example": "README.md"
        },
        "start_line": {
            "type": "integer",
            "example": 2
        },
        "end_line": {
            "type": "integer",
            "example": 2
        },
        "start_column": {
            "type": "integer",
            "example": 5,
            "nullable": true
        },
        "end_column": {
            "type": "integer",
            "example": 10,
            "nullable": true
        },
        "annotation_level": {
            "type": "string",
            "example": "warning",
            "nullable": true
        },
        "title": {
            "type": "string",
            "example": "Spell Checker",
            "nullable": true
        },
        "message": {
            "type": "string",
            "example": "Check your spelling for 'banaas'.",
            "nullable": true
        },
        "raw_details": {
            "type": "string",
            "example": "Do you mean 'bananas' or 'banana'?",
            "nullable": true
        },
        "blob_href": {
            "type": "string"
        }
    },
    "required": [
        "path",
        "blob_href",
        "start_line",
        "end_line",
        "start_column",
        "end_column",
        "annotation_level",
        "title",
        "message",
        "raw_details"
    ]
}
```

### `#/components/examples/check-annotation-items`

```json
{
    "value": [
        {
            "path": "README.md",
            "start_line": 2,
            "end_line": 2,
            "start_column": 5,
            "end_column": 10,
            "annotation_level": "warning",
            "title": "Spell Checker",
            "message": "Check your spelling for 'banaas'.",
            "raw_details": "Do you mean 'bananas' or 'banana'?",
            "blob_href": "https://api.github.com/repos/github/rest-api-description/git/blobs/abc"
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