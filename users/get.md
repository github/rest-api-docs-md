# List users

Lists all users, in the order that they signed up on GitHub. This list includes personal user accounts and organization accounts.

Note: Pagination is powered exclusively by the `since` parameter. Use the [Link header](https://docs.github.com/rest/guides/using-pagination-in-the-rest-api#using-link-headers) to get the URL for the next page of users.

## Operation Object

```json
{
    "summary": "List users",
    "description": "Lists all users, in the order that they signed up on GitHub. This list includes personal user accounts and organization accounts.\n\nNote: Pagination is powered exclusively by the `since` parameter. Use the [Link header](https://docs.github.com/rest/guides/using-pagination-in-the-rest-api#using-link-headers) to get the URL for the next page of users.",
    "tags": [
        "users"
    ],
    "operationId": "users/list",
    "externalDocs": {
        "description": "API method documentation",
        "url": "https://docs.github.com/rest/users/users#list-users"
    },
    "parameters": [
        {
            "$ref": "#/components/parameters/since-user"
        },
        {
            "$ref": "#/components/parameters/per-page"
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
                            "$ref": "#/components/schemas/simple-user"
                        }
                    },
                    "examples": {
                        "default": {
                            "$ref": "#/components/examples/simple-user-items"
                        }
                    }
                }
            },
            "headers": {
                "Link": {
                    "example": "<https://api.github.com/users?since=135>; rel=\"next\"",
                    "schema": {
                        "type": "string"
                    }
                }
            }
        },
        "304": {
            "$ref": "#/components/responses/not_modified"
        }
    },
    "x-github": {
        "githubCloudOnly": false,
        "enabledForGitHubApps": true,
        "category": "users",
        "subcategory": "users"
    }
}
```

## References

### `#/components/parameters/since-user`

```json
{
    "name": "since",
    "description": "A user ID. Only return users with an ID greater than this ID.",
    "in": "query",
    "required": false,
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

### `#/components/examples/simple-user-items`

```json
{
    "value": [
        {
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
    ]
}
```

### `#/components/responses/not_modified`

```json
{
    "description": "Not modified"
}
```