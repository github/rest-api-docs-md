# List branches for HEAD commit

Protected branches are available in public repositories with GitHub Free and GitHub Free for organizations, and in public and private repositories with GitHub Pro, GitHub Team, GitHub Enterprise Cloud, and GitHub Enterprise Server. For more information, see [GitHub's products](https://docs.github.com/github/getting-started-with-github/githubs-products) in the GitHub Help documentation.

Returns all branches where the given commit SHA is the HEAD, or latest commit for the branch.

## Operation Object

```json
{
    "summary": "List branches for HEAD commit",
    "description": "Protected branches are available in public repositories with GitHub Free and GitHub Free for organizations, and in public and private repositories with GitHub Pro, GitHub Team, GitHub Enterprise Cloud, and GitHub Enterprise Server. For more information, see [GitHub's products](https://docs.github.com/github/getting-started-with-github/githubs-products) in the GitHub Help documentation.\n\nReturns all branches where the given commit SHA is the HEAD, or latest commit for the branch.",
    "tags": [
        "repos"
    ],
    "operationId": "repos/list-branches-for-head-commit",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/commits/commits#list-branches-for-head-commit"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "$ref": "#/components/parameters/commit-sha"
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
                            "$ref": "#/components/schemas/branch-short"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/branch-short-items"
                        }
                    }
                }
            }
        },
        "422": {
            "$ref": "#/components/responses/validation_failed"
        },
        "409": {
            "$ref": "#/components/responses/conflict"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "commits",
        "subcategory": "commits"
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

### `#/components/parameters/commit-sha`

```json
{
    "name": "commit_sha",
    "description": "The SHA of the commit.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "string"
    },
    "x-multi-segment": true
}
```

### `#/components/schemas/branch-short`

```json
{
    "title": "Branch Short",
    "description": "Branch Short",
    "type": "object",
    "properties": {
        "name": {
            "type": "string"
        },
        "commit": {
            "type": "object",
            "properties": {
                "sha": {
                    "type": "string"
                },
                "url": {
                    "type": "string"
                }
            },
            "required": [
                "sha",
                "url"
            ]
        },
        "protected": {
            "type": "boolean"
        }
    },
    "required": [
        "name",
        "commit",
        "protected"
    ]
}
```

### `#/components/examples/branch-short-items`

```json
{
    "value": [
        {
            "name": "branch_5",
            "commit": {
                "sha": "c5b97d5ae6c19d5c5df71a34c7fbeeda2479ccbc",
                "url": "https://api.github.com/repos/octocat/Hello-World/commits/c5b97d5ae6c19d5c5df71a34c7fbeeda2479ccbc"
            },
            "protected": false
        }
    ]
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