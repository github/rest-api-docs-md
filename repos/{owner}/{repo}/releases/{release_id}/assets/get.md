# List release assets

`get /repos/{owner}/{repo}/releases/{release_id}/assets`



## Operation Object

```json
{
    "summary": "List release assets",
    "description": "",
    "tags": [
        "repos"
    ],
    "operationId": "repos/list-release-assets",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/releases/assets#list-release-assets"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/owner"
        },
        {
            "$ref": "#/components/parameters/repo"
        },
        {
            "$ref": "#/components/parameters/release-id"
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
                            "$ref": "#/components/schemas/release-asset"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/release-asset-items"
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
        "category": "releases",
        "subcategory": "assets"
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

### `#/components/parameters/release-id`

```json
{
    "name": "release_id",
    "description": "The unique identifier of the release.",
    "in": "path",
    "required": true,
    "schema": {
        "type": "integer"
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

### `#/components/schemas/release-asset`

```json
{
    "title": "Release Asset",
    "description": "Data related to a release.",
    "type": "object",
    "properties": {
        "url": {
            "type": "string",
            "format": "uri"
        },
        "browser_download_url": {
            "type": "string",
            "format": "uri"
        },
        "id": {
            "type": "integer"
        },
        "node_id": {
            "type": "string"
        },
        "name": {
            "description": "The file name of the asset.",
            "type": "string",
            "example": "Team Environment"
        },
        "label": {
            "type": "string",
            "nullable": true
        },
        "state": {
            "description": "State of the release asset.",
            "type": "string",
            "enum": [
                "uploaded",
                "open"
            ]
        },
        "content_type": {
            "type": "string"
        },
        "size": {
            "type": "integer"
        },
        "download_count": {
            "type": "integer"
        },
        "created_at": {
            "type": "string",
            "format": "date-time"
        },
        "updated_at": {
            "type": "string",
            "format": "date-time"
        },
        "uploader": {
            "$ref": "#/components/schemas/nullable-simple-user"
        }
    },
    "required": [
        "id",
        "name",
        "content_type",
        "size",
        "state",
        "url",
        "node_id",
        "download_count",
        "label",
        "uploader",
        "browser_download_url",
        "created_at",
        "updated_at"
    ]
}
```

### `#/components/examples/release-asset-items`

```json
{
    "value": [
        {
            "url": "https://api.github.com/repos/octocat/Hello-World/releases/assets/1",
            "browser_download_url": "https://github.com/octocat/Hello-World/releases/download/v1.0.0/example.zip",
            "id": 1,
            "node_id": "MDEyOlJlbGVhc2VBc3NldDE=",
            "name": "example.zip",
            "label": "short description",
            "state": "uploaded",
            "content_type": "application/zip",
            "size": 1024,
            "download_count": 42,
            "created_at": "2013-02-27T19:35:32Z",
            "updated_at": "2013-02-27T19:35:32Z",
            "uploader": {
                "login": "octocat",
                "id": 1,
                "node_id": "MDQ6VXNlcjE=",
                "avatar_url": "https://github.com/images/error/octocat_happy.gif",
                "gravatar_id": "",
                "url": "https://api.github.com/users/octocat",
                "html_url": "https://github.com/octocat",
                "followers_url": "https://api.github.com/users/octocat/followers",
                "following_url": "https://api.github.com/users/octocat/following{/other_user}",
                "gists_url": "https://api.github.com/users/octocat/gists{/gist_id}",
                "starred_url": "https://api.github.com/users/octocat/starred{/owner}{/repo}",
                "subscriptions_url": "https://api.github.com/users/octocat/subscriptions",
                "organizations_url": "https://api.github.com/users/octocat/orgs",
                "repos_url": "https://api.github.com/users/octocat/repos",
                "events_url": "https://api.github.com/users/octocat/events{/privacy}",
                "received_events_url": "https://api.github.com/users/octocat/received_events",
                "type": "User",
                "site_admin": false
            }
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