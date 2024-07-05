# List CODEOWNERS errors

List any syntax errors that are detected in the CODEOWNERS
file.

For more information about the correct CODEOWNERS syntax,
see "[About code owners](https://docs.github.com/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-code-owners)."

## Operation Object

```json
{
    "summary": "List CODEOWNERS errors",
    "description": "List any syntax errors that are detected in the CODEOWNERS\nfile.\n\nFor more information about the correct CODEOWNERS syntax,\nsee \"[About code owners](https://docs.github.com/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-code-owners).\"",
    "tags": [
        "repos"
    ],
    "operationId": "repos/codeowners-errors",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/repos/repos#list-codeowners-errors"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "name": "ref",
            "description": "A branch, tag or commit name used to determine which version of the CODEOWNERS file to use. Default: the repository's default branch (e.g. `main`)",
            "in": "query",
            "required": false,
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
                        "$ref": "#/components/schemas/codeowners-errors"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/codeowners-errors"
                        }
                    }
                }
            }
        },
        "404": {
            "description": "Resource not found"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "previews": [],
        "category": "repos",
        "subcategory": "repos"
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

### `#/components/schemas/codeowners-errors`

```json
{
    "title": "CODEOWNERS errors",
    "description": "A list of errors found in a repo's CODEOWNERS file",
    "type": "object",
    "properties": {
        "errors": {
            "type": "array",
            "items": {
                "type": "object",
                "properties": {
                    "line": {
                        "description": "The line number where this errors occurs.",
                        "type": "integer",
                        "example": 7
                    },
                    "column": {
                        "description": "The column number where this errors occurs.",
                        "type": "integer",
                        "example": 3
                    },
                    "source": {
                        "description": "The contents of the line where the error occurs.",
                        "type": "string",
                        "example": "* user"
                    },
                    "kind": {
                        "description": "The type of error.",
                        "type": "string",
                        "example": "Invalid owner"
                    },
                    "suggestion": {
                        "description": "Suggested action to fix the error. This will usually be `null`, but is provided for some common errors.",
                        "type": "string",
                        "nullable": true,
                        "example": "The pattern `/` will never match anything, did you mean `*` instead?"
                    },
                    "message": {
                        "description": "A human-readable description of the error, combining information from multiple fields, laid out for display in a monospaced typeface (for example, a command-line setting).",
                        "type": "string",
                        "example": "Invalid owner on line 7:\n\n  * user\n    ^"
                    },
                    "path": {
                        "description": "The path of the file where the error occured.",
                        "type": "string",
                        "example": ".github/CODEOWNERS"
                    }
                },
                "required": [
                    "line",
                    "column",
                    "kind",
                    "message",
                    "path"
                ]
            }
        }
    },
    "required": [
        "errors"
    ]
}
```

### `#/components/examples/codeowners-errors`

```json
{
    "value": {
        "errors": [
            {
                "line": 3,
                "column": 1,
                "kind": "Invalid pattern",
                "source": "***/*.rb @monalisa",
                "suggestion": "Did you mean `**/*.rb`?",
                "message": "Invalid pattern on line 3: Did you mean `**/*.rb`?\n\n  ***/*.rb @monalisa\n  ^",
                "path": ".github/CODEOWNERS"
            },
            {
                "line": 7,
                "column": 7,
                "kind": "Invalid owner",
                "source": "*.txt docs@",
                "suggestion": null,
                "message": "Invalid owner on line 7:\n\n  *.txt docs@\n        ^",
                "path": ".github/CODEOWNERS"
            }
        ]
    }
}
```