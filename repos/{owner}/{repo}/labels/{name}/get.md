# Get a label

Gets a label using the given name.

## Operation Object

```json
{
    "summary": "Get a label",
    "description": "Gets a label using the given name.",
    "tags": [
        "issues"
    ],
    "operationId": "issues/get-label",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/issues/labels#get-a-label"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "name": "name",
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
                        "$ref": "#/components/schemas/label"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/label"
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

### `#/components/examples/label`

```json
{
    "value": {
        "id": 208045946,
        "node_id": "MDU6TGFiZWwyMDgwNDU5NDY=",
        "url": "https://api.github.com/repos/octocat/Hello-World/labels/bug",
        "name": "bug",
        "description": "Something isn't working",
        "color": "f29513",
        "default": true
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