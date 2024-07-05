# List deploy keys

`get /repos/{owner}/{repo}/keys`



## Operation Object

```json
{
    "summary": "List deploy keys",
    "description": "",
    "tags": [
        "repos"
    ],
    "operationId": "repos/list-deploy-keys",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/deploy-keys/deploy-keys#list-deploy-keys"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
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
                            "$ref": "#/components/schemas/deploy-key"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/deploy-key-items"
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
        "category": "deploy-keys",
        "subcategory": "deploy-keys"
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

### `#/components/schemas/deploy-key`

```json
{
    "title": "Deploy Key",
    "description": "An SSH key granting access to a single repository.",
    "type": "object",
    "properties": {
        "id": {
            "type": "integer"
        },
        "key": {
            "type": "string"
        },
        "url": {
            "type": "string"
        },
        "title": {
            "type": "string"
        },
        "verified": {
            "type": "boolean"
        },
        "created_at": {
            "type": "string"
        },
        "read_only": {
            "type": "boolean"
        },
        "added_by": {
            "type": "string",
            "nullable": true
        },
        "last_used": {
            "type": "string",
            "nullable": true
        }
    },
    "required": [
        "id",
        "key",
        "url",
        "title",
        "verified",
        "created_at",
        "read_only"
    ]
}
```

### `#/components/examples/deploy-key-items`

```json
{
    "value": [
        {
            "id": 1,
            "key": "ssh-rsa AAA...",
            "url": "https://api.github.com/repos/octocat/Hello-World/keys/1",
            "title": "octocat@octomac",
            "verified": true,
            "created_at": "2014-12-10T15:53:42Z",
            "read_only": true,
            "added_by": "octocat",
            "last_used": "2022-01-10T15:53:42Z"
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