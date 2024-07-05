# Get latest Pages build

`get /repos/{owner}/{repo}/pages/builds/latest`

Gets information about the single most recent build of a GitHub Pages site.

OAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "Get latest Pages build",
    "description": "Gets information about the single most recent build of a GitHub Pages site.\n\nOAuth app tokens and personal access tokens (classic) need the `repo` scope to use this endpoint.",
    "tags": [
        "repos"
    ],
    "operationId": "repos/get-latest-pages-build",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/pages/pages#get-latest-pages-build"
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
            "description": "Response",
            "content": {
                "application/json": {
                    "schema": {
                        "$ref": "#/components/schemas/page-build"
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/page-build"
                        }
                    }
                }
            }
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "pages",
        "subcategory": "pages"
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

### `#/components/schemas/page-build`

```json
{
    "title": "Page Build",
    "description": "Page Build",
    "type": "object",
    "properties": {
        "url": {
            "type": "string",
            "format": "uri"
        },
        "status": {
            "type": "string"
        },
        "error": {
            "type": "object",
            "properties": {
                "message": {
                    "type": "string",
                    "nullable": true
                }
            },
            "required": [
                "message"
            ]
        },
        "pusher": {
            "$ref": "#/components/schemas/nullable-simple-user"
        },
        "commit": {
            "type": "string"
        },
        "duration": {
            "type": "integer"
        },
        "created_at": {
            "type": "string",
            "format": "date-time"
        },
        "updated_at": {
            "type": "string",
            "format": "date-time"
        }
    },
    "required": [
        "url",
        "status",
        "error",
        "pusher",
        "commit",
        "duration",
        "created_at",
        "updated_at"
    ]
}
```

### `#/components/examples/page-build`

```json
{
    "value": {
        "url": "https://api.github.com/repos/github/developer.github.com/pages/builds/5472601",
        "status": "built",
        "error": {
            "message": null
        },
        "pusher": {
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
        },
        "commit": "351391cdcb88ffae71ec3028c91f375a8036a26b",
        "duration": 2104,
        "created_at": "2014-02-10T19:00:49Z",
        "updated_at": "2014-02-10T19:00:51Z"
    }
}
```