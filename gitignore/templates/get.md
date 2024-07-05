# Get all gitignore templates

`get /gitignore/templates`

List all templates available to pass as an option when [creating a repository](https://docs.github.com/rest/repos/repos#create-a-repository-for-the-authenticated-user).

## Operation Object

```json
{
    "summary": "Get all gitignore templates",
    "description": "List all templates available to pass as an option when [creating a repository](https://docs.github.com/rest/repos/repos#create-a-repository-for-the-authenticated-user).",
    "operationId": "gitignore/get-all-templates",
    "tags": [
        "gitignore"
    ],
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/gitignore/gitignore#get-all-gitignore-templates"
    },
    "parameters": [],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "type": "array",
                        "items": {
                            "type": "string"
                        }
                    },
                    "examples": {
                        "default": {
                            "value": [
                                "Actionscript",
                                "Android",
                                "AppceleratorTitanium",
                                "Autotools",
                                "Bancha",
                                "C",
                                "C++"
                            ]
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

### `#/components/responses/not_modified`

```json
{
    "description": "Not modified"
}
```