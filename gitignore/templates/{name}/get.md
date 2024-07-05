# Get a gitignore template

Get the content of a gitignore template.

This endpoint supports the following custom media types. For more information, see "[Media types](https://docs.github.com/rest/using-the-rest-api/getting-started-with-the-rest-api#media-types)."

- **`application/vnd.github.raw+json`**: Returns the raw .gitignore contents.

## Operation Object

```json
{
    "summary": "Get a gitignore template",
    "description": "Get the content of a gitignore template.\n\nThis endpoint supports the following custom media types. For more information, see \"[Media types](https://docs.github.com/rest/using-the-rest-api/getting-started-with-the-rest-api#media-types).\"\n\n- **`application/vnd.github.raw+json`**: Returns the raw .gitignore contents.",
    "operationId": "gitignore/get-template",
    "tags": [
        "gitignore"
    ],
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/gitignore/gitignore#get-a-gitignore-template"
    },
    "parameters": [
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
                        "$ref": "#/components/schemas/gitignore-template"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/gitignore-template"
                        }
                    }
                }
            }
        },
        "304": {
            "$ref": "#/components/responses/not_modified"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "gitignore",
        "subcategory": "gitignore"
    }
}
```

## References

### `#/components/schemas/gitignore-template`

```json
{
    "title": "Gitignore Template",
    "description": "Gitignore Template",
    "type": "object",
    "properties": {
        "name": {
            "type": "string",
            "example": "C"
        },
        "source": {
            "type": "string",
            "example": "# Object files\n*.o\n\n# Libraries\n*.lib\n*.a\n\n# Shared objects (inc. Windows DLLs)\n*.dll\n*.so\n*.so.*\n*.dylib\n\n# Executables\n*.exe\n*.out\n*.app\n"
        }
    },
    "required": [
        "name",
        "source"
    ]
}
```

### `#/components/examples/gitignore-template`

```json
{
    "value": {
        "name": "C",
        "source": "# Object files\n*.o\n\n# Libraries\n*.lib\n*.a\n\n# Shared objects (inc. Windows DLLs)\n*.dll\n*.so\n*.so.*\n*.dylib\n\n# Executables\n*.exe\n*.out\n*.app\n"
    }
}
```

### `#/components/responses/not_modified`

```json
{
    "description": "Not modified"
}
```