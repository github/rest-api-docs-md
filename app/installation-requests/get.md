# List installation requests for the authenticated app

Lists all the pending installation requests for the authenticated GitHub App.

## Operation Object

```json
{
    "summary": "List installation requests for the authenticated app",
    "description": "Lists all the pending installation requests for the authenticated GitHub App.",
    "tags": [
        "apps"
    ],
    "operationId": "apps/list-installation-requests-for-authenticated-app",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/apps/apps#list-installation-requests-for-the-authenticated-app"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/per-page"
        },
        {
            "$ref": "#/components/parameters/page"
        }
    ],
    "responses": {
        "200": {
            "description": "List of integration installation requests",
            "content": {
                "application/json": {
                    "schema": {
                        "type": "array",
                        "items": {
                            "$ref": "#/components/schemas/integration-installation-request"
                        }
                    },
                    "examples": {
                        "exampleKey1": {
                            "$ref": "#/components/examples/integration-installation-request-paginated"
                        }
                    }
                }
            }
        },
        "304": {
            "$ref": "#/components/responses/not_modified"
        },
        "401": {
            "$ref": "#/components/responses/requires_authentication"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "apps",
        "subcategory": "apps"
    }
}
```

## References

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

### `#/components/schemas/integration-installation-request`

```json
{
    "title": "Integration Installation Request",
    "description": "Request to install an integration on a target",
    "type": "object",
    "properties": {
        "id": {
            "description": "Unique identifier of the request installation.",
            "type": "integer",
            "example": 42
        },
        "node_id": {
            "type": "string",
            "example": "MDExOkludGVncmF0aW9uMQ=="
        },
        "account": {
            "anyOf": [
                {
                    "$ref": "#/components/schemas/simple-user"
                },
                {
                    "$ref": "#/components/schemas/enterprise"
                }
            ]
        },
        "requester": {
            "$ref": "#/components/schemas/simple-user"
        },
        "created_at": {
            "type": "string",
            "format": "date-time",
            "example": "2022-07-08T16:18:44-04:00"
        }
    },
    "required": [
        "id",
        "account",
        "requester",
        "created_at"
    ]
}
```

### `#/components/examples/integration-installation-request-paginated`

```json
{
    "value": [
        {
            "id": 25381,
            "node_id": "MDEyOkludGVncmF0aW9uMTIzNDU2Nzg5MA==",
            "account": {
                "login": "octo-org",
                "id": 6811672,
                "node_id": "MDEyOk9yZ2FuaXphdGlvbjY4MTE2NzI=",
                "avatar_url": "https://avatars3.githubusercontent.com/u/6811672?v=4",
                "gravatar_id": "",
                "url": "https://api.github.com/users/octo-org",
                "html_url": "https://github.com/octo-org",
                "followers_url": "https://api.github.com/users/octo-org/followers",
                "following_url": "https://api.github.com/users/octo-org/following{/other_user}",
                "gists_url": "https://api.github.com/users/octo-org/gists{/gist_id}",
                "starred_url": "https://api.github.com/users/octo-org/starred{/owner}{/repo}",
                "subscriptions_url": "https://api.github.com/users/octo-org/subscriptions",
                "organizations_url": "https://api.github.com/users/octo-org/orgs",
                "repos_url": "https://api.github.com/users/octo-org/repos",
                "events_url": "https://api.github.com/users/octo-org/events{/privacy}",
                "received_events_url": "https://api.github.com/users/octo-org/received_events",
                "type": "Organization",
                "site_admin": false
            },
            "requester": {
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
            "created_at": "2022-07-08T16:18:44-04:00"
        }
    ]
}
```

### `#/components/responses/not_modified`

```json
{
    "description": "Not modified"
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