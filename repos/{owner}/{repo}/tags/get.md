# List repository tags

`get /repos/{owner}/{repo}/tags`



## Operation Object

```json
{
    "summary": "List repository tags",
    "description": "",
    "tags": [
        "repos"
    ],
    "operationId": "repos/list-tags",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/repos/repos#list-repository-tags"
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
                            "$ref": "#/components/schemas/tag"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/tag-items"
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

### `#/components/schemas/tag`

```json
{
    "title": "Tag",
    "description": "Tag",
    "type": "object",
    "properties": {
        "name": {
            "type": "string",
            "example": "v0.1"
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
        "zipball_url": {
            "type": "string",
            "format": "uri",
            "example": "https://github.com/octocat/Hello-World/zipball/v0.1"
        },
        "tarball_url": {
            "type": "string",
            "format": "uri",
            "example": "https://github.com/octocat/Hello-World/tarball/v0.1"
        },
        "node_id": {
            "type": "string"
        }
    },
    "required": [
        "name",
        "node_id",
        "commit",
        "zipball_url",
        "tarball_url"
    ]
}
```

### `#/components/examples/tag-items`

```json
{
    "value": [
        {
            "name": "v0.1",
            "commit": {
                "sha": "c5b97d5ae6c19d5c5df71a34c7fbeeda2479ccbc",
                "url": "https://api.github.com/repos/octocat/Hello-World/commits/c5b97d5ae6c19d5c5df71a34c7fbeeda2479ccbc"
            },
            "zipball_url": "https://github.com/octocat/Hello-World/zipball/v0.1",
            "tarball_url": "https://github.com/octocat/Hello-World/tarball/v0.1",
            "node_id": "MDQ6VXNlcjE="
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