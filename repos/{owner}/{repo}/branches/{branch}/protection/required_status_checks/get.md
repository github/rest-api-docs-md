# Get status checks protection

Protected branches are available in public repositories with GitHub Free and GitHub Free for organizations, and in public and private repositories with GitHub Pro, GitHub Team, GitHub Enterprise Cloud, and GitHub Enterprise Server. For more information, see [GitHub's products](https://docs.github.com/github/getting-started-with-github/githubs-products) in the GitHub Help documentation.

## Operation Object

```json
{
    "summary": "Get status checks protection",
    "description": "Protected branches are available in public repositories with GitHub Free and GitHub Free for organizations, and in public and private repositories with GitHub Pro, GitHub Team, GitHub Enterprise Cloud, and GitHub Enterprise Server. For more information, see [GitHub's products](https://docs.github.com/github/getting-started-with-github/githubs-products) in the GitHub Help documentation.",
    "tags": [
        "repos"
    ],
    "operationId": "repos/get-status-checks-protection",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/branches/branch-protection#get-status-checks-protection"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "$ref": "#/components/parameters/branch"
        }
    ],
    "responses": {
        "200": {
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/status-check-policy"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/status-check-policy"
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
        "category": "branches",
        "subcategory": "branch-protection"
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

### `#/components/parameters/branch`

```json
{
    "name": "branch",
    "description": "The name of the branch. Cannot contain wildcard characters. To use wildcard characters in branch names, use [the GraphQL API](https://docs.github.com/graphql).",
    "in": "path",
    "required": true,
    "schema": {
        "type": "string"
    },
    "x-multi-segment": true
}
```

### `#/components/schemas/status-check-policy`

```json
{
    "title": "Status Check Policy",
    "description": "Status Check Policy",
    "type": "object",
    "properties": {
        "url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/repos/octocat/Hello-World/branches/master/protection/required_status_checks"
        },
        "strict": {
            "type": "boolean",
            "example": true
        },
        "contexts": {
            "type": "array",
            "example": [
                "continuous-integration/travis-ci"
            ],
            "items": {
                "type": "string"
            }
        },
        "checks": {
            "type": "array",
            "items": {
                "type": "object",
                "properties": {
                    "context": {
                        "type": "string",
                        "example": "continuous-integration/travis-ci"
                    },
                    "app_id": {
                        "type": "integer",
                        "nullable": true
                    }
                },
                "required": [
                    "context",
                    "app_id"
                ]
            }
        },
        "contexts_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/repos/octocat/Hello-World/branches/master/protection/required_status_checks/contexts"
        }
    },
    "required": [
        "url",
        "contexts_url",
        "strict",
        "contexts",
        "checks"
    ]
}
```

### `#/components/examples/status-check-policy`

```json
{
    "value": {
        "url": "https://api.github.com/repos/octocat/Hello-World/branches/master/protection/required_status_checks",
        "strict": true,
        "contexts": [
            "continuous-integration/travis-ci"
        ],
        "contexts_url": "https://api.github.com/repos/octocat/Hello-World/branches/master/protection/required_status_checks/contexts"
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