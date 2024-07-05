# Check if automated security fixes are enabled for a repository

`get /repos/{owner}/{repo}/automated-security-fixes`

Shows whether automated security fixes are enabled, disabled or paused for a repository. The authenticated user must have admin read access to the repository. For more information, see "[Configuring automated security fixes](https://docs.github.com/articles/configuring-automated-security-fixes)".

## Operation Object

```json
{
    "summary": "Check if automated security fixes are enabled for a repository",
    "description": "Shows whether automated security fixes are enabled, disabled or paused for a repository. The authenticated user must have admin read access to the repository. For more information, see \"[Configuring automated security fixes](https://docs.github.com/articles/configuring-automated-security-fixes)\".",
    "tags": [
        "repos"
    ],
    "operationId": "repos/check-automated-security-fixes",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/repos/repos#check-if-automated-security-fixes-are-enabled-for-a-repository"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        }
    ],
    "responses": {
        "200": {
            "description": "Response if dependabot is enabled",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/check-automated-security-fixes"
                    },
                    "examples": {
                        "default": {
                            "value": {
                                "enabled": true,
                                "paused": false
                            }
                        }
                    }
                }
            }
        },
        "404": {
            "description": "Not Found if dependabot is not enabled for the repository"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
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

### `#/components/schemas/check-automated-security-fixes`

```json
{
    "title": "Check Automated Security Fixes",
    "description": "Check Automated Security Fixes",
    "type": "object",
    "properties": {
        "enabled": {
            "type": "boolean",
            "example": true,
            "description": "Whether automated security fixes are enabled for the repository."
        },
        "paused": {
            "type": "boolean",
            "example": false,
            "description": "Whether automated security fixes are paused for the repository."
        }
    },
    "required": [
        "enabled",
        "paused"
    ]
}
```