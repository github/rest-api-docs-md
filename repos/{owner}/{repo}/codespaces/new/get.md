# Get default attributes for a codespace

Gets the default attributes for codespaces created by the user with the repository.

OAuth app tokens and personal access tokens (classic) need the `codespace` scope to use this endpoint.

## Operation Object

```json
{
    "summary": "Get default attributes for a codespace",
    "description": "Gets the default attributes for codespaces created by the user with the repository.\n\nOAuth app tokens and personal access tokens (classic) need the `codespace` scope to use this endpoint.",
    "tags": [
        "codespaces"
    ],
    "operationId": "codespaces/pre-flight-with-repo-for-authenticated-user",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/codespaces/codespaces#get-default-attributes-for-a-codespace"
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
            "description": "The branch or commit to check for a default devcontainer path. If not specified, the default branch will be checked.",
            "in": "query",
            "schema": {
                "type": "string",
                "example": "main"
            }
        },
        {
            "name": "client_ip",
            "description": "An alternative IP for default location auto-detection, such as when proxying a request.",
            "in": "query",
            "schema": {
                "type": "string",
                "example": "1.2.3.4"
            }
        }
    ],
    "responses": {
        "200": {
            "description": "Response when a user is able to create codespaces from the repository.",
            "content": {
                "application/json": {
                    "schema": {
                        "type": "object",
                        "properties": {
                            "billable_owner": {
                                "$ref": "#/components/schemas/simple-user"
                            },
                            "defaults": {
                                "type": "object",
                                "required": [
                                    "location",
                                    "devcontainer_path"
                                ],
                                "properties": {
                                    "location": {
                                        "type": "string"
                                    },
                                    "devcontainer_path": {
                                        "type": "string",
                                        "nullable": true
                                    }
                                }
                            }
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/codespaces-default-attributes-for-a-codespace"
                        }
                    }
                }
            }
        },
        "401": {
            "$ref": "#/components/responses/requires_authentication"
        },
        "403": {
            "$ref": "#/components/responses/forbidden"
        },
        "404": {
            "$ref": "#/components/responses/not_found"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "codespaces",
        "subcategory": "codespaces"
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

### `#/components/schemas/simple-user`

```json
{
    "title": "Simple User",
    "description": "A GitHub user.",
    "type": "object",
    "properties": {
        "name": {
            "nullable": true,
            "type": "string"
        },
        "email": {
            "nullable": true,
            "type": "string"
        },
        "login": {
            "type": "string",
            "example": "octocat"
        },
        "id": {
            "type": "integer",
            "format": "int64",
            "example": 1
        },
        "node_id": {
            "type": "string",
            "example": "MDQ6VXNlcjE="
        },
        "avatar_url": {
            "type": "string",
            "format": "uri",
            "example": "https://github.com/images/error/octocat_happy.gif"
        },
        "gravatar_id": {
            "type": "string",
            "example": "41d064eb2195891e12d0413f63227ea7",
            "nullable": true
        },
        "url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/users/octocat"
        },
        "html_url": {
            "type": "string",
            "format": "uri",
            "example": "https://github.com/octocat"
        },
        "followers_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/users/octocat/followers"
        },
        "following_url": {
            "type": "string",
            "example": "https://api.github.com/users/octocat/following{/other_user}"
        },
        "gists_url": {
            "type": "string",
            "example": "https://api.github.com/users/octocat/gists{/gist_id}"
        },
        "starred_url": {
            "type": "string",
            "example": "https://api.github.com/users/octocat/starred{/owner}{/repo}"
        },
        "subscriptions_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/users/octocat/subscriptions"
        },
        "organizations_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/users/octocat/orgs"
        },
        "repos_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/users/octocat/repos"
        },
        "events_url": {
            "type": "string",
            "example": "https://api.github.com/users/octocat/events{/privacy}"
        },
        "received_events_url": {
            "type": "string",
            "format": "uri",
            "example": "https://api.github.com/users/octocat/received_events"
        },
        "type": {
            "type": "string",
            "example": "User"
        },
        "site_admin": {
            "type": "boolean"
        },
        "starred_at": {
            "type": "string",
            "example": "\"2020-07-09T00:17:55Z\""
        }
    },
    "required": [
        "avatar_url",
        "events_url",
        "followers_url",
        "following_url",
        "gists_url",
        "gravatar_id",
        "html_url",
        "id",
        "node_id",
        "login",
        "organizations_url",
        "received_events_url",
        "repos_url",
        "site_admin",
        "starred_url",
        "subscriptions_url",
        "type",
        "url"
    ]
}
```

### `#/components/examples/codespaces-default-attributes-for-a-codespace`

```json
{
    "value": {
        "billable_owner": {
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
        "defaults": {
            "location": "EastUs",
            "devcontainer_path": ".devcontainer/devcontainer.json"
        }
    }
}
```

### `#/components/responses/requires_authentication`

```json
{
    "description": "Requires authentication",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/basic-error"
            }
        }
    }
}
```

### `#/components/responses/forbidden`

```json
{
    "description": "Forbidden",
    "content": {
        "application/json": {
            "schema": {
                "$ref": "#/components/schemas/basic-error"
            }
        }
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