# List branches



## Operation Object

```json
{
    "summary": "List branches",
    "description": "",
    "tags": [
        "repos"
    ],
    "operationId": "repos/list-branches",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/branches/branches#list-branches"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "name": "protected",
            "description": "Setting to `true` returns only branches protected by branch protections or rulesets. When set to `false`, only unprotected branches are returned. Omitting this parameter returns all branches.",
            "in": "query",
            "required": false,
            "schema": {
                "type": "boolean"
            }
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
                            "$ref": "#/components/schemas/short-branch"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/short-branch-with-protection-items"
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
        "404": {
            "$ref": "#/components/responses/not_found"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "branches",
        "subcategory": "branches"
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

### `#/components/schemas/short-branch`

```json
{
    "title": "Short Branch",
    "description": "Short Branch",
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
                    "type": "string",
                    "format": "uri"
                }
            },
            "required": [
                "sha",
                "url"
            ]
        },
        "protected": {
            "type": "boolean"
        },
        "protection": {
            "$ref": "#/components/schemas/branch-protection"
        },
        "protection_url": {
            "type": "string",
            "format": "uri"
        }
    },
    "required": [
        "name",
        "commit",
        "protected"
    ]
}
```

### `#/components/examples/short-branch-with-protection-items`

```json
{
    "value": [
        {
            "name": "master",
            "commit": {
                "sha": "c5b97d5ae6c19d5c5df71a34c7fbeeda2479ccbc",
                "url": "https://api.github.com/repos/octocat/Hello-World/commits/c5b97d5ae6c19d5c5df71a34c7fbeeda2479ccbc"
            },
            "protected": true,
            "protection": {
                "required_status_checks": {
                    "enforcement_level": "non_admins",
                    "contexts": [
                        "ci-test",
                        "linter"
                    ]
                }
            },
            "protection_url": "https://api.github.com/repos/octocat/hello-world/branches/master/protection"
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